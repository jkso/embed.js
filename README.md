Embed-js
============

Embed-js has evolved from a simple text emoticon to image emoji conversion system into a fully-blown text beautification toolkit.

Besides taking emoticons expressed using a text form and converting them to icon font-based or image-based emojis, this plugin can also do some other stuff too..

The demo examples are given [here](http://rkritesh.in/embed-js)

**The angular version of this plugin is [ngEmbed](http://github.com/ritz078/ngEmbed)**

Contents
--------
* [Features](#features)
* [Dependencies](#dependencies)
* [Getting Started](#getting-started)
* [HTML Structure](#html-structure)
* [Usage Example](#usage-example)
* [Advanced Options](#advanced-options)
* [Examples](http://rkritesh.in/embed-js)

Features
--------

* Converts emoticon text codes into emoticons :smile: , :heart:
* Finds links in text input and turns them into html links.
* Youtube and Vimeo video embedding with video details fetched from the api.
* HTML5 player supported media embedding (mp3,mp4,ogg)
* PDF viewing with preview and then the actual pdf in a frame.
* Inline Code Syntax highlighting (uses highlight.js)
* Twitter tweet embedding supported
* Codepen, jsbin,ideone, jsfiddle and plunker embed supported
* soundcloud and spotify support
* Twitch tv, dotSub, dailymotion, vine,TED and liveLeak support.
* Google map location embed

Dependencies
------------
* Jquery >= 1.2
* [Highlight.js](https://highlightjs.org/) (Optional if code syntax highlighting is needed)
* [Twitter widgets.js](http://platform.twitter.com/widgets.js) (Optional if tweet embed support is set to true needed)

Getting started
---------------

Bower
```
bower install --save embed-js
```

npm
```
npm install --save embed-js
```

Load css file
```html
<link rel="stylesheet" href="path/to/jquery.embed.css"/>
```

Load Scripts
```html
<script src="path/to/jquery.min.js"></script>
<!--==== Optional =====-->
<script src="https://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.4/highlight.min.js"></script>
<script src="http://platform.twitter.com/widgets.js"></script>
<!--===================-->
<script src="path/to/jquery.embed.js"></script>
```

HTML Structure
--------------
```html
<div id="element">
  <div> Some content here </div>
  <div> Some content here </div>
  ...
  ...
</div>
```

Usage Example
-------------
```html
<script>
$('#element').embedJS({
    gdevAuthKey : 'xxxxxxxx'
});
</script>
```
This is the minimal setup in which all features will work in their default configuration.If you want to disable any feature or change any default setting see below.

Advanced Options
----------------
Only **gdevAuth** option is mandatory. Other options provide you additional control on the plugin.
The below setting shows all the default values.

```html
<script>
$('#element').embedJS({
      //Instructs the library whether or not to embed urls
      link              : true,
      //same as the target attribute in html anchor tag . supports all html supported target values.
      linkTarget        : '_blank',
      //Array of extensions to be excluded from converting into links
      linkExclude       : ['jpg','pdf'],
      //set false to show a preview of pdf links
      pdfEmbed          : true,
      //set false to embed images
      imageEmbed        : true,
      //set false to embed audio
      audioEmbed        : false,
      //set false to show a preview of youtube/vimeo videos with details
      videoEmbed        : true,
      //set false to show basic video files like mp4 etc. (supported by html5 player)
      basicVideoEmbed   : true,
      //width of the video frame (in pixels)
      videoWidth        : 640,
      //height of the video frame (in pixels)
      videoHeight       : 390,
      //( Mandatory ) The authorization key obtained from google's developer console for
      //using youtube data api and map embed api
      gdevAuthKey         : 'xxxxxxx',
      //Set google map location embed
      // Use @(place-name) to use this feature . Eg: @(Sydney)
      locationEmbed       :true,
      //Instructs the library whether or not to highlight code syntax.
      highlightCode     : true,
      //Instructs the library whether or not embed the tweets
      tweetsEmbed     : true,
      tweetOptions:{
            //The maximum width of a rendered Tweet in whole pixels. Must be between 220 and 550 inclusive.
            maxWidth   : 550,
            //When set to true or 1 links in a Tweet are not expanded to photo, video, or link previews.
            hideMedia  : false,
            //When set to true or 1 a collapsed version of the previous Tweet in a conversation thread
            //will not be displayed when the requested Tweet is in reply to another Tweet.
            hideThread : false,
            //Specifies whether the embedded Tweet should be floated left, right, or center in
            //the page relative to the parent element.Valid values are left, right, center, and none.
            //Defaults to none, meaning no alignment styles are specified for the Tweet.
            align      : 'none',
            //Request returned HTML and a rendered Tweet in the specified.
            //Supported Languages listed here (https://dev.twitter.com/web/overview/languages)
            lang       : 'en'
      },
      //set false to embed codepen
      codepenEmbed      :true,
      //codepen height (width can be adjusted by css)
      codepenHeight     :300,
      //set false to embed jsfiddle
      jsfiddleEmbed     :true,
      //jsfiddle height (width can be adjusted by css)
      jsfiddleHeight    :300,
      //set false to embed jsbin
      jsbinEmbed        :true,
      //jsbin height (width can be adjusted by css)
      jsbinHeight       :300,
      //set false to embed ideone
      ideoneEmbed       :true,
      //ideone height (width can be adjusted by css)
      ideoneHeight      :300,
      plunkerEmbed      :true,
      plunkerHeight     :300,
      spotifyEmbed     :true,
      //set false to embed soundcloud
      soundCloudEmbed  : true,
      soundCloudOptions: {
          height      : 160,
          themeColor  : 'f50000',    //Hex Code of the player theme color
          autoPlay    : false,
          hideRelated : false,
          showComments: true,
          showUser    : true,        //Show or hide the uploader name, useful e.g. in tiny players to save space)
          showReposts : false,
          visual      : false,       //Show/hide the big preview image
          download    : false        //Show/Hide download buttons
              },
      twitchtvEmbed     :true,
      dotsubEmbed       :true,
      dailymotionEmbed  :true,
      vineEmbed        : true,
      vineOptions:{
            width:500,
            type:'postcard'         //'postcard' or 'simple' embedding
      },
      tedEmbed         :true,
      liveleakEmbed     :true,
      //callback before pdf preview
      beforePdfPreview  : function(){},
      //callback after pdf preview
      afterPdfPreview   : function(){},
      // callback on video frame view
      onVideoShow:function(){},
      //callback on video load (youtube/vimeo)
      onVideoLoad:function(){}

});
</script>
```
If you specify either one of **videoWidth** or **videoHeight** , the other option will be automatically set in the aspected ratio.

Examples
--------

Visit [http://rkritesh.in/embed-js](http://rkritesh.in/embed-js)

Version 2.0.2
-------------
* Ideone and plunker support added
* Code comments added


Contributing
------------

Before sending a pull request remember to follow [jQuery Core Style Guide](http://contribute.jquery.org/style-guide/js/).

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Make your changes on the `src` folder, never on the `dist` folder.
4. Commit your changes: `git commit -m 'Add some feature'`
5. Push to the branch: `git push origin my-new-feature`
6. Submit a pull request :smile:

License
-------

```
The MIT License (MIT)
Copyright (c) 2014 Ritesh Kumar

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```


