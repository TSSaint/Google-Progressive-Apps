# Google-Progressive-Apps
## What is A Progressive App?
Progressive Apps are web applications that work regardless of a user's internet connection quality.<br>
A common problem occurs when users are left waiting for data and are literally left unaware of whether or not their application is working. <br>

## The Usual Pattern - and a Problem
When using a web app say, on a phone, a couple of things occur. Generally, the phone sends a request through wifi/cell towers, through the ISP, some proxies, and finally the destination (a server). Afterwards, the reverse occurs, and data renders on the phone - the application "works".<br>
However, several factors can break this pattern, such as - crowding, cell tower failure, and environmental occurences. Additionally, if any single step is affected, the end user will be affected and the app will seemingly be "broken", or in connection limbo.
<br>
Some things that cause a poor user experience:
-Poor signal
-Fault in mobile network
-DDoS'd server
-Bug in the server
-Physics (like the moon's gravitational pull)

## Benefits of Offline-First Design
A strategy that deals with common network failures that hurt user's experiences is to design offline first. Offline-first is a "godl-standard approach" that more or less renders data that stems from a user's cached device data and such. The application grabs from a cache first, and is updated if content arrives from the network. Ultimately, this creates a continued and unbroken user experience - it's a "good" illusion that keeps the web experience happy, even if the network is actually experiencing problems.
<br>
Some offline-first strategies:
-Pulling page content from the device cache, displaying "something" to a user, then try to get content from the network
-Deliver live chat data and allow the user to interact with other users, then try to update the interactions when network connection is reistablished
-Render a page header from the cache and fetch content from the network

## Service Worker
Service worker is a software (usually Javascript) and a relatively new browser feature that "sits" between the device/page, invisible to the user/can't acess the DOM, and intercepts requests as the browser makes them. One way to use this is to store the page activity in a cache while waiting for the network to return information.
<br>
This is just of the few ways to call Service Worker:<br>
```js
// Need an understanding of JS Promises to utilize
navigator.serviceWorker.register('/sw.js').then(function(reg) {
  console.log('One');
}).catch(function(err) {
  console.log('Two');
});
``` 
Service worker will control any page URL that begins with a specified scope by default. SW specifies URLS one "slash" deep, like so (an example using scope):<br>
```js
navigator.serviceWorker.register('/sw.js', {scope: '/foo/'});
// will apply to URLs deeper than foo, but not foo
// Ex. /foo/bar, /foo/index.html, /foo.html
```

We can check if a browser supports Service Worker by visiting: https://jakearchibald.github.io/isserviceworkerready/ 
