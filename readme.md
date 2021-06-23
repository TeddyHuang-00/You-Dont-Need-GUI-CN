# 有了 CLI，还要什么 GUI

[![加入Spectrum社群（英文）](https://withspectrum.github.io/badge/badge.svg)](https://spectrum.chat/you-dont-need/GUI)

<details>
给新手用的命令行常用工具介绍 :)
</details>
<br/>

图形用户操作界面（Graphical User Interfaces, GUI）对用户很友好，易于上手，没有命令行操作界面（Command-Line Interfaces, CLI）这么陡峭的学习曲线。

![Xerox Star 8010 工作站](./Xerox_Star_8010_workstations.jpg)

但事实上，他们通常会消耗更多的计算资源，并且在自动化处理方面不如 CLI 那么容易且强大。

作为计算机专家，我们希望工作做得又快又好。当然我们也知道各种“黑话”一样的命令行可能不那么容易发现或者记住，所以我们试着在这儿列举一些常见的 GUI 操作是如何在 CLI 实现的。

<h2> 快速跳转 </h2>

- [拷贝一个文件](#拷贝一个文件)
- [创建文件副本](#创建文件副本)
- [拷贝一个目录](#拷贝一个目录)
- [创建目录副本](#创建目录副本)
- [移动一个文件](#移动一个文件)
- [重命名文件](#重命名文件)
- [移动一个目录](#移动一个目录)
- [重命名目录](#重命名目录)
- [merge directories](#merge-directories)
- [create a new file](#create-a-new-file)
- [create a new directory](#create-a-new-directory)
- [show file/directory size](#show-filedirectory-size)
- [show file/directory info](#show-filedirectory-info)
- [open a file with the default program](#open-a-file-with-the-default-program)
- [zip a directory](#zip-a-directory)
- [unzip a directory](#unzip-a-directory)
- [peek files in a zip file](#peek-files-in-a-zip-file)
- [remove a file](#remove-a-file)
- [remove a directory](#remove-a-directory)
- [list directory contents](#list-directory-contents)
- [tree view a directory and its subdirectories](#tree-view-a-directory-and-its-subdirectories)
- [find a stale file](#find-a-stale-file)
- [show a calendar](#show-a-calendar)
- [find a future date](#find-a-future-date)
- [use a calculator](#use-a-calculator)
- [force quit a program](#force-quit-a-program)
- [check server response](#check-server-response)
- [view content of a file](#view-content-of-a-file)
- [search for a text](#search-for-a-text)
- [view an image](#view-an-image)
- [show disk size](#show-disk-size)
- [check performance of your computer](#check-performance-of-your-computer)
- [Quick tips](#quick-tips)
- [Hotkeys](#hotkeys)
- [I can't remember these cryptic commands](#i-cant-remember-these-cryptic-commands)

## 拷贝一个文件

**别再用拖拽或者 `CMD`/`CTRL` + `C`, `CMD`/`CTRL` + `V` 来复制文件了！** :-1:

将 `readme.txt` 拷贝到 `documents` 目录下

```shell
$ cp readme.txt documents/
```

## 创建文件副本

**不要再用`右键`来创建副本了！** :-1:

```shell
$ cp readme.txt readme.bak.txt
```

更高级的写法：

```shell
$ cp readme{,.bak}.txt
# 注: 注意这里的 {} 起什么作用，可以试试 touch foo{1,2,3}.txt 然后看看结果如何
```

## 拷贝一个目录

**也别拖拽目录了，也不要 `CMD`/`CTRL` + `C`, `CMD`/`CTRL` + `V` 来拷贝目录了！** :-1:

把 `myMusic` 整个目录拷贝到 `myMedia` 目录下面

```shell
$ cp -a myMusic myMedia/
# 或者你也可以写成
$ cp -a myMusic/ myMedia/myMusic/
```

## 创建目录副本

**也别用`右键`来创建目录副本了** :-1:

```shell
$ cp -a myMusic/ myMedia/
# 如果 `myMedia` 文件夹不存在的话
$ cp -a myMusic myMedia/
```

## 移动一个文件

**没有什么拖拽文件，也没有 `CMD`/`CTRL` + `X`, `CMD`/`CTRL` + `V` 来剪切** :-1:

```shell
$ mv readme.txt documents/
```

**一定** 要在移动文件时在目标目录的最后加上斜杠`/`。（[不然的话](http://unix.stackexchange.com/a/50533)，简言之会被当作[这样](#重命名文件)）

## 重命名文件

**别用`右键`-`重命名`了！** :-1:

```shell
$ mv readme.txt README.md
```

## 移动一个目录

**没有了拖拽文件夹，也没有 `CMD`/`CTRL` + `X`, `CMD`/`CTRL` + `V`** :-1:

```shell
$ mv myMedia myMusic/
# 或者也可以写成
$ mv myMedia/ myMusic/myMedia
```

## 重命名目录

**也别`右键`文件夹然后`重命名`了** :-1:

```shell
$ mv myMedia/ myMusic/
```

## merge directories

**STOP DRAG AND DROPPING TO MERGE DIRECTORIES** :-1:

```shell
$ rsync -a /images/ /images2/	# note: may over-write files with the same name, so be careful!
```

## create a new file

**STOP RIGHT CLICKING AND CREATE A NEW FILE** :-1:

```shell
$ touch 'new file'    # updates the file's access and modification timestamp if it already exists
# or
$ > 'new file'        # note: erases the content if it already exists
```

## create a new directory

**STOP RIGHT CLICKING AND CREATE A NEW DIRECTORY** :-1:

```shell
$ mkdir 'untitled folder'
# or
$ mkdir -p 'path/may/not/exist/untitled\ folder'
```

## show file/directory size

**STOP RIGHT CLICKING AND SHOW FILE/directory INFO** :-1:

```shell
$ du -sh node_modules/
```

## show file/directory info

**STOP RIGHT CLICKING AND SHOW FILE/DIRECTORY INFO** :-1:

```shell
$ stat -x readme.md   # on macOS
$ stat readme.md      # on Linux
```

## open a file with the default program

**STOP DOUBLE CLICKING ON A FILE** :-1:

```shell
$ xdg-open file   # on Linux
$ open file       # on MacOS
```

## zip a directory

**STOP RIGHT CLICKING AND COMPRESS DIRECTORY** :-1:

```shell
$ zip -r archive_name.zip folder_to_compress
```

## unzip a directory

**STOP RIGHT CLICKING AND UNCOMPRESS DIRECTORY** :-1:

```shell
$ unzip archive_name.zip
```

## peek files in a zip file

**STOP USING WinRAR** :-1:

```shell
$ zipinfo archive_name.zip
# or
$ unzip -l archive_name.zip
```

## remove a file

**STOP RIGHT CLICKING AND DELETE A FILE PERMANENTLY** :-1:

```shell
$ rm my_useless_file
```

IMPORTANT: The rm command deletes my_useless_file permanently, which is equivalent to move my_useless_file to Recycle Bin and hit Empty Recycle Bin.

## remove a directory

**STOP RIGHT CLICKING AND DELETE A DIRECTORY PERMANENTLY** :-1:

```shell
$ rm -r my_useless_folder
```

## list directory contents

**STOP OPENING YOUR FINDER OR FILE EXPLORER** :-1:

```shell
$ ls my_folder        # Simple
$ ls -la my_folder    # -l: show in list format. -a: show all files, including hidden. -la combines those options.
$ ls -alrth my_folder # -r: reverse output. -t: sort by time (modified). -h: output human-readable sizes.
```

## tree view a directory and its subdirectories

**STOP OPENING YOUR FINDER OR FILE EXPLORER** :-1:

```shell
$ tree                                                        # on Linux
$ find . -print | sed -e 's;[^/]*/;|____;g;s;____|; |;g'      # on MacOS
# Note: install homebrew (https://brew.sh) to be able to use (some) Linux utilities such as tree.
# brew install tree
```

## find a stale file

**STOP USING YOUR FILE EXPLORER TO FIND A FILE** :-1:

Find all files modified more than 5 days ago

```shell
$ find my_folder -mtime +5
```

## show a calendar

**STOP LOOKING UP WHAT THIS MONTH LOOKS LIKE BY CALENDAR WIDGETS** :-1:

Display a text calendar

```shell
$ cal
```

Display selected month and year calendar

```shell
$ cal 11 2018
```

## find a future date

**STOP USING WEBAPPS TO CALCULATE FUTURE DATES** :-1:

What is todays date?

```shell
$ date +%m/%d/%Y
```

What about a week from now?

```shell
$ date -d "+7 days"                                           # on Linux
$ date -j -v+7d                                               # on MacOS
```

## use a calculator

**STOP USING CALCULATOR WIDGET** :-1:

```shell
$ bc
```

## force quit a program

**STOP CTRL + ALT + DELETE and choose the program to kill** :-1:

```shell
$ killall program_name
```

## check server response

**STOP OPENING A BROWSER** :-1:

```shell
curl -i umair.surge.sh
# curl's -i (--include) option includes HTTP response headers in its output.
```

## view content of a file

**STOP DOUBLE CLICKING A FILE** :-1:

```shell
$ cat apps/settings.py
# if the file is too big to fit on one page, you can use a 'pager' (less) which shows you one page at a time.
$ less apps/settings.py
```

## search for a text

**STOP CMD/CTRL + F IN A DIRECTORY** :-1:

```shell
$ grep -i "Query" file.txt
```

![grep](./grep.jpg)

## view an image

**STOP USING PREVIEW** :-1:

```shell
$ imgcat image.png
# Note: requires iTerm2 terminal.
```

## show disk size

**STOP RIGHT CLICKING DISK ICON OR OPENING DISK UTILITY** :-1:

```shell
$ df -h
```

## check performance of your computer

**STOP OPENING YOUR ACTIVITY MONITOR OR TASK MANAGER** :-1:

```shell
$ top
```

## Quick tips

![CLI tips](./cli_tips.jpg)

## Hotkeys

```
Ctrl + A  Go to the beginning of the line you are currently typing on
Ctrl + E  Go to the end of the line you are currently typing on
Ctrl + L  Clears the Screen, similar to the clear command
Ctrl + U  Clears the line before the cursor position. If you are at the end of the line, clears the entire line.
Ctrl + H  Same as backspace
Ctrl + R  Lets you search through previously used commands
Ctrl + C  Kill whatever you are running
Ctrl + D  Exit the current shell
Ctrl + Z  Puts whatever you are running into a suspended background process. fg restores it.
Ctrl + W  Delete the word before the cursor
Ctrl + K  Clear the line after the cursor
Ctrl + T  Swap the last two characters before the cursor
Esc + T   Swap the last two words before the cursor
Alt + F   Move cursor forward one word on the current line
Alt + B   Move cursor backward one word on the current line
Tab       Auto-complete files and directory names
```

## I can't remember these cryptic commands

You can always google or `man` the commands you are not familiar with. Or, checkout [tldr](https://github.com/tldr-pages/tldr), a collection of simplified and community-driven man pages.
