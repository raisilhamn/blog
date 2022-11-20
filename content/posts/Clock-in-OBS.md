---
title: "Clock in OBS"
date: 2022-11-20T20:18:15+07:00
draft: true

tags: ["Utility"]
author: "Me"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
comments: false
description: "Desc Text."
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
---

Import lewat browser lalu masukan file. 

Clock.html

```html 
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title>A simple clock</title>
  </head>

  <body translate="no">
    <div
      id="output"
      style="
        display: inline-block;
        font-family: monospace;
        font-size: 30px;
        text-align: right;
        color: lightgray;
        border-radius: 10px;
        padding: 10px;
        background-color: rgba(0, 0, 0, 0.75);
      "
    ></div>

    <script src="https://cdnjs.cloudflare.com/ajax/libs/moment.js/2.18.1/moment.min.js"></script>
    <script>
      // https://stackoverflow.com/questions/901115/how-can-i-get-query-string-values-in-javascript
      var urlParams;
      (function () {
        var match,
          pl = /\+/g, // Regex for replacing addition symbol with a space
          search = /([^&=]+)=?([^&]*)/g,
          decode = function (s) {
            return decodeURIComponent(s.replace(pl, " "));
          },
          query = window.location.search.substring(1);
        urlParams = {};
        while ((match = search.exec(query)))
          urlParams[decode(match[1])] = decode(match[2]);
      })();
      var output = document.getElementById("output");
      if (urlParams["style"]) output.setAttribute("style", urlParams["style"]);
      if (urlParams["bodyStyle"])
        document.body.setAttribute("style", urlParams["bodyStyle"]);
      var c;
      setInterval(
        (c = function () {
          output.innerText = moment().format(
            urlParams["format"] || "DD/MM/YYYY HH:mm:ss"
          );
        }),
        1000
      );
      c();
    </script>
  </body>
</html>
```

