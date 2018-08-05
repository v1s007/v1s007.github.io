---
layout:     post
title:      同步visualStudioCode设置
subtitle:   让VisualStudioCode设置跟随你-在每个机器上都有熟悉的环境
date:       2018-08-05
author:     LZP[整理]
header-img: img/bg-it3.jpg
catalog: true
tags:
    - visual Studio Code
    - 插件
---

> * setting Sync是Visual Source Code的一个插件，可以通过你的github账户的gist来保存Visual Source Code的各种设置，重装机器、换到其它机器，都可以随时切换到自己熟悉的Visual Source Code环境。
> 
> * setting Sync的安装非常简单，打开Visual Source Code的“扩展”侧边栏，输入"setting Sync"查找，找到点击安装即可。
> 
> *  也可以直接打开这个[链接地址](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync)，点击“install"(安装)。
> 
> * 本人安装成功，同步visual source code的设置到github gist，可[参考](https://gist.github.com/longzeping/30076e10f9423df34b88445a2920fcc5)
> 
> * 安装和使用中，如果有疑问，欢迎在本文后面留言！

## Settings Sync

> Previously known as Visual Studio Code Settings Sync
>
> Type Sync in command Palette in order to view all commands.

#### Key Features

1. Use your GitHub account token and Gist.
2. Easy to Upload and Download on one click.
3. Show a summary page at the end with details about config and extensions effected.
4. Auto Download Latest Settings on Startup.
5. Auto upload Settings on file change.
6. Share the Gist with other users and let them download your settings.
7. Supports GitHub Enterprise

#### It Syncs

All extensions and complete User Folder that Contains
1. Settings File
2. Keybinding File
3. Launch File
4. Snippets Folder
5. VSCode Extensions Settings
6. Workspaces Folder

#### Shortcuts

1. Upload Key : Shift + Alt + U
2. Download Key : Shift + Alt + D


#### Steps To Get a Personal Access Token from GitHub

This extension requires a Personal Access Token from your GitHub account. You can create one by simply following the steps shown in the pictures below. Make sure you add Gist in scope.

1. Go to Settings / Developer settings / Personal access tokens / Generate New Token
2. Select Gist From Scopes.
3. Get an Access Token.

#### Upload Your Settings For the first time

* Press Shift + Alt + U it will ask your GitHub account access token.
 
* Type ">Sync" In Command Palette into order download / upload
 
* This will automatically open your GitHub settings page, allowing you to generate a new token for the application, as explained in the previous section. This token will allow the extension to create gists.

* Enter the GitHub token in the window and click enter.

* Upload your settings automatically and the extension gives you Gist ID in the system message. Gist ID is needed to access the data you have uploaded with your token. Copy this Gist ID in order to download the settings to other machines.

* You can always verify created gist on the following url:https://gist.github.com/{your_userName}/{gist_id}

* Here is the gif of the complete process when you execute the Upload command (Might take some time to load)

#### Download your Settings

1. Press Shift + Alt + D it will ask your GitHub Gist ID.

2. Type ">Sync" In Command Palette into order download / upload

3. Enter Your GitHub Token.

4. Enter the GitHub token in the window and click enter.Enter Your Gist ID.

5. You need to enter your Gist ID in order to download the files you have uploaded with Shift + Alt + U.

6. Settings Downloaded. You are Done! All your files are downloaded


#### Reset Token / Gist Settings

Type ">Sync" In Command Palette and select Reset Token and Gist Settings

#### Toggle Auto Download

Auto Download is disabled by default. It will sync all the setting by default when the editor starts. Please make sure you have valid github Token and Gist available to make it work properly.

Select Command "Sync : Advanced Options > Toggle Auto-Download On Startup" command to Turn ON / OFF the auto download.

#### Toggle Force Download

Force Download is disabled by default. By default, extension won't download the latest settings if you already have the latest downloaded version, but sometimes when you delete some extension locally and don't upload the settings it will still show that you have latest versions by date or time checks, by turning this ON it will always download the cloud settings on startup.

Please make sure you have valid github Token and Gist available to make it work properly.

Select Command "Sync : Advanced Options > Toggle Force Download" command to Turn ON / OFF the force download.

#### Toggle Auto-Upload on change

Auto-upload is disabled by default. When the settings are changed and saved this feature will automatically start the upload process and save the settings online.

Please make sure you have valid github Token and Gist available to make it work properly.

Select Command "Sync : Advanced Options > Toggle Auto-Upload on Settings Change" command to Turn ON / OFF the auto-upload.

#### Toggle Summary

Summary is enabled by default which shows all files and extensions that are added or deleted on a single page. You may turn it off in order to make a upload and download process clean and quiet.

Select Command "Sync : Advanced Options > Show Summary Page On Upload / Download" command to Turn ON / OFF the auto download.

#### Create Public Gist To Share Settings

By default, it creates secret Gist so only you can see it but if you want to share your Gist with other users, you can set it to public. You can't change the exiting Gist type from secret to public so it will reset the Gist ID so you can create new Gist with all existing editor settings.

Select Command "Sync : Advanced Options > Share Settings with Public GIST"

Other users can give your Gist Id to download the Gist, but they can't upload their settings on your Gist.

#### Settings

For details regarding settings keys, click here

    "sync.gist": "0c929b1a6c51015cdc9e0fe2e369ea4c",
    "sync.lastUpload": "2018-03-04T14:21:39.841Z",
    "sync.autoDownload": false,
    "sync.autoUpload": false,
    "sync.lastDownload": "2018-03-04T14:21:39.841Z",
    "sync.forceDownload": true,
    "sync.host": "",
    "sync.pathPrefix": "",
    "sync.quietSync": false,
    "sync.askGistName": false,
    "sync.removeExtensions": true,
    "sync.syncExtensions": true

#### Customized Sync

Extension will create the syncLocalSettings.json inside User folder upon code start. 
On Windows, this is %APPDATA%\Code\User\syncLocalSettings.json. 
Mac, $HOME/Library/Application Support/Code/User/syncLocalSettings.json. 
Linux, ~/.config/Code/User/syncLocalSettings.json. 

You can customize the sync:

1. Options by which files / folders and settings to exclude from upload.
2. The Gist Description when creating new Gist.
3. Replace the code settings after downloading.
4. Change the Gist description while creating new one in github.

The JSON will be created as:

{
    "ignoreUploadFiles": [ "projects.json", "projects_cache_vscode.json",
        "projects_cache_git.json", "projects_cache_svn.json", "gpm_projects.json",
        "gpm-recentItems.json"
    ],
    "ignoreUploadFolders": [
        "workspaceStorage"
    ],
    "ignoreExtensions": [
        "ignored_extension_name"
    ],
    "replaceCodeSettings": {
         "http.proxy": "http://my.proxy.address:8080"
    },
    "gistDescription": "Visual Studio Code Settings Sync Gist",
    "version": 290,
    "token": "YOUR_GITHUB_TOKEN_HERE",
    "downloadPublicGist": false,
    "supportedFileExtensions": [
        "json", "code-snippets"
    ]
}

For settings details, visit my post [here](https://medium.com/@itsShanKhan/visual-studio-code-settings-sync-configurations-ed8dd6fd9753)
