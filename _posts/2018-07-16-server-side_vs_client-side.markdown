---
layout: post
title:      "Server-Side vs Client-Side"
date:       2018-07-16 21:21:58 +0000
permalink:  server-side_vs_client-side
---


Back in the early 2000's, nearly all websites were built to use server-side rendering. When a new page (or small change) was requested, the browser would send a request back for the new data. The server would respond with a whole new resource for the browser to load, and the cycle would repeat itself every time a user asked for something. This meant little interactivity and full page reloads, but did offer a more straightforward SEO schema. But those were the days before websites were more like apps. 

Now, Javascript frameworks are used unanimously to provide consumers with rich, interactive, data-driven websites and apps. Javascript is primarily a client-side technology, meaning that the rendering is done on the consumer's machine without going back to our servers and requiring a full page reload. 

Enter ```remote: true```! Remote true is a server-generated Javascript pattern in which the browser simply asks for instructions when users make requests. The server then provides new instructions (new Javascript) for the browser to operate upon. In this pattern, the initial page load time is still quick because you aren't having to load in all the JS files for each new full reload. But it also gives you some benefits on over pure client-side rendering, since it gives you access to .erb tools like Ruby variables, helpers, and partials.




