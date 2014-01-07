---
layout: post
title:  "Ex 1 Pt 2 - Status Icon"
date:   2014-01-07 23:17:00
categories: youtube browser-plugin firefox widget
---

First thing on (not so long) list of features will be status icon.
I've decided to use standard firefox widget for that purpose.

The downside of this approach is that (at least in firefox 26) there
is no way to set initial location of widget icon. Default location
is lower right corner. Obviously I would like to place it next to download 
button/icon. Of course when I find solution I will post it here.

Nevertheless, lets assume that the icon will have three states (at least for
now):

- there is no possible download on page - gray icon,
- tab currently being watched contain youtube player - red icon,
- displayed video is already downloade in at least one quality version - green icon.

{% highlight javascript %}
// Used as a listener of events
var tabs = require("sdk/tabs");

// Used for loading the icons
var data = require("sdk/self").data;

var widget = require("sdk/widget").Widget({
    id: "moldur-youtube-downloader",
    label: "YouTube Download",
    contentURL: data.url("down-arrow-gray.png")
});

// Observe tab switch or document changes in each existing tab:
function updateWidgetState(tab) {
    var view = widget.getView(tab.window);
    if (!view) return;
    // Update widget displayed icon
    view.contentURL = tab.url.match(/www\.youtube\..*\/watch\?v=/) ? 
        data.url("down-arrow-red.png") : data.url("down-arrow-gray.png");
}

// Executes update function tab ready and active
tabs.on('ready', updateWidgetState);
tabs.on('activate', updateWidgetState);
{% endhighlight %}

Code showed above places gray download icon in the lower right corner
of the browser - the bottom addon bar. When in currently displayed tab url 
matches given regexp - `/www\.youtube\..*\/watch\?v=/` - icon changes its
color to red. It means that user can click the icon and chose desired
quality version of the video to download. Which obviusly doesn't work yet.

See next part, wher I shall add popup panel when the icon is red.

