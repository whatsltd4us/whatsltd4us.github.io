---
layout: post
title:  "Client Side Rendering Vs Server Side Rendering in React js"
date:   2020-05-06 00:00:00 +0700
categories: react
---
### 1. What is Client Side Rendering?
<img src='https://raw.githubusercontent.com/whatsltd4us/whatsltd4us.github.io/master/_assets/images/client-side-redering.png'/>

Client-side rendering is a reasonably new approach to rendering websites, and it didn’t really become popular until JavaScript libraries started incorporating it.  
When we talk about client-side rendering, it’s about rendering content in the browser using JavaScript. So instead of getting all the content from the HTML document itself, a bare-bones HTML document with a JavaScript file in initial loading itself is received, which renders the rest of the site using the browser.
With client-side rendering, the initial page load is naturally a bit slow. However, after that, every subsequent page load is very fast. In this approach, communication with server happens only for getting the run-time data. Moreover, there is no need to reload the entire UI after every call to the server. The client-side framework manages to update UI with changed data by re-rendering only that particular DOM element.  

### 2. What is Server Side Rendering ?
<img src='https://raw.githubusercontent.com/whatsltd4us/whatsltd4us.github.io/master/_assets/images/server-side-redering.png'/>

In server-side rendering when a user makes a request to a webpage, the server prepares an HTML page by fetching user-specific data and sends it to the user’s machine over the internet. The browser then constructs the content and displays the page. This entire process of fetching data from the database, creating an HTML page and sending it to client happens in mere milliseconds.  

### 3. Server Side Rendering Vs Client Side Rendering. 
The main difference is that for SSR your service response to the browser is the HTML of your page that is ready to be rendered,while for CSR the browser gets a pretty empty documents which links to your javaScript. That means your browser will start rendering the HTML from your server without having to wait for all the javaScript to be downloaded and executed ,In both cases , React will need to be downloads and go through the same process of building a virtual DOM and attaching events to make the page interactive but for SSR,the user can start viewing the page while all of that is happening .For the CSR world you need to want for all of the above to happen and then the virtual DOM moved to the browser DOM for the page to be view able.  

#### Pros of Server Side Rendering :
1. Search engines can crawl the site for better SEO.
2. The initial page load is faster.
3. Great for static sites.

#### Cons of Server Side Rendering:
1. Frequent server requests.
2. An overall slow page rendering.
3. Full page reloads.
4. Non-rich site interactions

#### Pros of Client Side Rendering:
1. Rich site interactions
2. Fast website rendering after the initial load.
3. Great for web applications.
4. Robust selection of JavaScript libraries.

#### Cons of Client Side Rendering:
1. Low SEO if not implemented correctly.
2. Initial load might require more time.
3. In most cases, requires an external library.



