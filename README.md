ℹ INFO:  Jan 2019

-

-modified share, now it is possible to view share like user's file(not only download), added separate menu. Possible to restrict share to the specific users, all registered users, or all users(even not registered).

-db and cli replaced with one single config file. When you create a new user for the first time, set "firstRun":true, this will read "open/not hashed" password, and replace it with hash.

-added possibility to auth by list of ip addresses. Change "auth.method":"ip" in order to enable. Available values:ip, proxy, none, default(login and password)

-updated build command, in order to reduce final binary size. Please rebuild with debug info before submit bug report.

-removed file type detection based on content.

-removed user commands after/before file upload ...

-removed thirdparty archive, now there is system dependency on zip tool. It will call bash and redirect zip output stream directly to the browser, bypass any buffers.

-successfully run on home router with MediaTek MT7621AT CPU

-currently preview generation limited by only images, and videos, you can disable it at all by changing "defaultUser.allowGeneratePreview".

-dependencies update: filebrowser.conf(path next to the binary, required), convert.sh(path next to the binary, only if you use previews), zip linux tool(only for downloads), and ffmpeg(only if you use previews)


ℹ INFO: Nov 25 2018,  after tries to use nextcloud as a home cloud, it was not possible to use it due to performance issues. So I've decided to adopt filebrowser project to my needs. Here it is list of things I've done:

-added thumbnail generation, it requires ffmpeg as system dependencies, limited generation only for images and videos

-added thumbnails user path at settings, and by default it must be set with "-v" short command. This path, should be <b>out</b> of the user's file scope path, otherwise it will recursively generate previews for self!

-added better file type detection at the backend

-integrated photoswipe as image slider and aplayer as audio player, and left default slider for other file types.

-added possibility to play music folder recursively by selecting required folders, and press music icon at the top. Mentioned button will play current folder without recursion. APlayer hidden by default

-deleted staticgen


planned to do:

-share permanent folders as separate path in menu between all users

-make docker image with required dependencies

-make ARM/MIPS docker images

-focus modifications to fit ARM/MIPS(low resources) architectures





ℹ INFO: **This project is not under active development ATM. A small group of developers keeps the project alive, but due to lack of time, we can't continue adding new features or doing deep changes. Please read [#532](https://github.com/filebrowser/filebrowser/issues/532) for more info!**

ℹ INFO: in Q2 2018, this project was renamed from `filemanager` to `filebrowser`, and the main repo was moved from [hacdias/filemanager](https://github.com/hacdias/filemanager) to [filebrowser/filebrowser](https://github.com/filebrowser/filebrowser). At the same time, the official docker image was changed to [`filebrowser/filebrowser`](https://hub.docker.com/r/filebrowser/filebrowser/). Users are encouraged to check their sources and update them accordingly.

---

<p align="center">
  <img src="https://raw.githubusercontent.com/filebrowser/logo/master/banner.png" width="550"/>
</p>

![Preview](https://user-images.githubusercontent.com/5447088/28537288-39be4288-70a2-11e7-8ce9-0813d59f46b7.gif)

# filebrowser

[![Travis](https://img.shields.io/travis/com/filebrowser/filebrowser.svg?style=flat-square)](https://travis-ci.com/filebrowser/filebrowser)
[![Go Report Card](https://goreportcard.com/badge/github.com/filebrowser/filebrowser?style=flat-square)](https://goreportcard.com/report/github.com/filebrowser/filebrowser)
[![Documentation](https://img.shields.io/badge/godoc-reference-blue.svg?style=flat-square)](http://godoc.org/github.com/filebrowser/filebrowser)
[![Version](https://img.shields.io/github/release/filebrowser/filebrowser.svg?style=flat-square)](https://github.com/filebrowser/filebrowser/releases/latest)
[![Chat IRC](https://img.shields.io/badge/freenode-%23filebrowser-blue.svg?style=flat-square)](http://webchat.freenode.net/?channels=%23filebrowser)

filebrowser provides a file managing interface within a specified directory and it can be used to upload, delete, preview, rename and edit your files. It allows the creation of multiple users and each user can have its own directory. It can be used as a standalone app or as a middleware.

# Table of contents

+ [Getting started](#getting-started)
+ [Features](#features)
  - [Users](#users)
  - [Search](#search)
+ [Contributing](#contributing)
+ [Donate](#donate)

# Getting started

You can find the Getting Started guide on the [documentation](https://filebrowser.github.io/quick-start/).

# Features

Easy login system.

![Login Page](https://user-images.githubusercontent.com/5447088/42046516-fe702976-7af5-11e8-9d72-c996150b09f5.png)

Listings of your files, available in two styles: mosaic and list. You can delete, move, rename, upload and create new files, as well as directories. Single files can be downloaded directly, and multiple files as *.zip*, *.tar*, *.tar.gz*, *.tar.bz2* or *.tar.xz*.

![Mosaic Listing](https://user-images.githubusercontent.com/5447088/42046515-fe3f7d58-7af5-11e8-8f87-270947ed755f.png)

File Browser editor is powered by [Codemirror](https://codemirror.net/) and if you're working with markdown files with metadata, both parts will be separated from each other so you can focus on the content.

![Markdown Editor](https://user-images.githubusercontent.com/5447088/42046519-ff17b81c-7af5-11e8-90f3-184e0ad24b7c.png)

On the settings page, a regular user can set its own custom CSS to personalize the experience and change its password. For admins, they can manage the permissions of each user, set commands which can be executed when certain events are triggered (such as before saving and after saving) and change plugin's settings.

![Settings](https://user-images.githubusercontent.com/5447088/42046517-fea206e4-7af5-11e8-88fe-b88513b43f43.png)

We also allow the users to search in the directories and execute commands if allowed.

## Users

We support multiple users and each user can have its own scope and custom stylesheet. The administrator is able to choose which permissions should be given to the users, as well as the commands they can execute. Each user also have a set of rules, in which he can be prevented or allowed to access some directories (regular expressions included!).

![Users](https://user-images.githubusercontent.com/5447088/42046518-fed14440-7af5-11e8-9a57-f4a611e9598d.png)

## Search

File Browser allows you to search through your files and it has some options. By default, your search will be something like this:

```
this are keywords
```

If you search for that it will look at every file that contains "this", "are" or "keywords" on their name. If you want to search for an exact term, you should surround your search by double quotes:

```
"this is the name"
```

That will search for any file that contains "this is the name" on its name. It won't search for each separated term this time.

By default, every search will be case insensitive. Although, you can make a case sensitive search by adding `case:sensitive` to the search terms, like this:

```
this are keywords case:sensitive
```

# Contributing

The contributing guidelines can be found [here](https://github.com/filebrowser/community).
