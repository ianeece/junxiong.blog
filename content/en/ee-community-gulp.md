---
lang: en
slug: ee-community-gulp
title: So you want to try another way to programing EarthEngine javascript code
date: 2017-04-23
tags: EarthEngine
---
<!-- more -->
![](http://oouh9u8nz.bkt.gdipper.com//ee-community-gulp.jpg)

[EarthEngine Code Editor](https://code.earthengine.google.com/)  is a web-based IDE for the Earth Engine JavaScript API.  It provides a variety of fantastic features including: 

1. Generated map tiles for instantaneous display (which is the WOO HOO feature of EE)
1. Query objects placed on the map with the Inspector tab. 
1. [Display and chart numeric results](https://developers.google.com/earth-engine/charts.html) using the Google Visualization API. 
1. Share a unique URL to your script with collaborators with the Get Link button. 

The bottleneck is that it is a pain to build big script with Javascript API because you have to copy all the functions into a single javascript file. Code Editor is a IDE which is designed for quick-test and prototype-development, not a IDE to maintenance a function of list, beautify/reformat the code, manage a lot of snippets (it based on googlesource, which will become very slow if you have a lot of snippets in a repo). But, if you move to Python API, hoping to enhance these aspects while coding, you have to sacrifice the above good things.

So for a long term I am seeking for a way which can help me organize my function and snippets in a manageable way:
[ee-community-gulp](https://github.com/gee-community/ee-community-gulp)

It can enable you to define some including files, which means you can put you common functions/code into single files, and include them into your main program when needed.  For example, I put all my function to operation ee.Image and ee.ImageCollection into file named eec.image.js. And in it there is a function named eec.image.sentinel2, which can generate sentinel-2 ImageCollection every 16-day (it will be useful if you want to do some time series analysis and it contain some simple cloud remove code).

Now I want to re-use eec.image.sentinel2 in another file,  ex1.js,  so I just need to include the file in the beginning, like:

```javascript
//=require ../eec.image.js 
var collect = eec.image.sentinel2('2016-6-1’, '2016-7-1’)
```

After the require statement I can call the function by name.

In order to use it, you have to clone the [repo](https://github.com/gee-community/ee-community-gulp) from github and following the installation guide. You need [node.js](https://nodejs.org/en/) as dependency.
If you work under Linux and Mac OS X then you can make some shortcut with [sed](https://www.gnu.org/software/sed/manual/sed.html) and [pbcopy](http://osxdaily.com/2007/03/05/manipulating-the-clipboard-from-the-command-line/). If not you can still use it with some extra simple operations.

You are welcome to let me know which function you will like to contain in the including files.

Itiya correction.
