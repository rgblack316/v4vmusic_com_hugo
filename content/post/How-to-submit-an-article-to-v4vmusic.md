---
title: 'How to Submit an Article to V4vmusic'
author: 
date: 2023-10-19T16:04:40-07:00
categories:
  - 'v4vMusicSite'
  - 'Tutorials'
tags:
  - ''
menu: 'main'
toc: true
thumbnail: ''
---

This site uses the [Hugo](https://gohugo.io/documentation/) content management system and is hosted on [github](https://github.com/v4vmusic/v4vmusic_com_hugo).

## Clone the Repo

Fork the github repo [https://github.com/v4vmusic/v4vmusic_com_hugo](https://github.com/v4vmusic/v4vmusic_com_hugo)

Then clone your forked repo to your machine.

`git clone git@github.com:<YOUR-GITHUB-ACCOUNT>/v4vmusic_com_hugo.git`

Create a new branch for you to work in

`git branch <new-branch>`

Checkout your new branch

`git checkout <new-branch>`


## Write your Article
Now that you have a working local git repo you can write your article using the [Markdown](https://www.markdownguide.org/) format. I recommend using the [Obsidian](https://obsidian.md/) editor as it's freaking awesome!

make a copy of the file `v4vmusic_com_hugo/submitted/template.md`
and rename it to `v4vmusic_com_hugo/submitted/title-of-your-article.md`

Open `v4vmusic_com_hugo/submitted/title-of-your-article.md` in your favorite text editor and begin typing. Be sure to fill out the information at the top of the file. Save your work.

If you're using Obsidian there are a few extra steps but in my opinion well worth it.

Open `v4vmusic_com_hugo/submitted/title-of-your-article.md` in your favorite text editor.

Select everything `Ctrl-A` 

Copy everything `Ctrl-C`

then in Hugo create a new note and paste into it.

Start writing away, when you are finished again copy everything from Obsidian and past into your favorite text editor.

Make sure to save the file as `title-of-your-article.md` in the `v4vmusic_com_hugo/submitted/` folder


## Commit Your Changes and Submit

On the command line execute the following command

`git add .`

`git commit -m 'Submitting my article title-of-your-article.md'`

`git push`

## Submit a Pull Request
Go to your github account and submit a pull request
If your pull request is accepted then someone with proper access will review your article and add it to the website

