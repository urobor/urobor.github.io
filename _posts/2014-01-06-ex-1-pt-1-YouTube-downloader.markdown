---
layout: post
title:  "Ex 1 Pt 1 - YouTube Downloader"
date:   2014-01-06 18:27:00
categories: youtube browser-plugin firefox chrome
---

As a part of my current activities I've decided to develop some simple
plugin for Firefox (later, maybe in Chrome, just for comparison).

The task was to make plugin for Firefox which will be able to:

- download video currently being displayed (one/two clicks from page
with the video),
- keep the record of already downloaded videos:
  - show simple indicator (an icon) - downloaded/not downloaded,
  - show list of downloaded versions,
- allow user to download other (not downloaded yet) versions.

First approach was about changing the YouTube html content and adding
some menu bar representing status and available versions. Below screen
from not downloaded yet video.

![Menu element image](/img/ex-1-pt1-old-dwn-clean-vid.png "Clean video downloader v.0.1")

The main problem with that approach was the YouTube page itself. As not very
expirienced with dynamic web content, "page" was simply deleting added html 
content. Quickest workaround was setting the delay of DOM modifications 
to x (actually 8) secounds, which was to long to wait for download status
icon to show up (ugly and simply unacceptable). Final version will be using
only browser UI: panel, menu bar, etc.

Below another image of working alpha version. This time with two versions
of the video already downloaded. 

![Menu element image](/img/ex-1-pt1-old-dwn-downloaded-vid.png "Already downloaded example")


This kind of functionality will be transfered to version with UI based on
browser build-in widgets and panels. See part-2.

