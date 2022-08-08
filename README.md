# Tampermonkey "One-Stop-Shop"


On this page you will find all of the information you need to know about how to use [TamperMonkey](https://www.tampermonkey.net/) to create a custom Sitecore CDP/P demo.


## What is a "tampermonkey demo?

This kind of custom demo allows you to:
 1. Show data capture in Sitecore CDP/P on any website
 2. Publish Web Experiences on any website
 3. Publish and trigger Full Stack Experiences on any website

## Installing Tampermonkey

[Tampermonkey](https://www.tampermonkey.net/) is a browser (Chrome, Firefox etc.) plugin. Just check their docs or Google or Youtube to figure out how to install the plugin.

## Installing the Sitecore CDP/P JS library on a website with Tampermonkey

To run a custom tampermonkey demo on a prospects website first you need to use tampermonkey to "install" the Sitecore CDP/P JS library on your target website.

Use either of these 2 tampermonkey scripts to 'install' the Sitecore CDP/P JS library on a website.

1. https://github.com/rjzflynnbx/tampermonkey-script/blob/main/script.js
2. https://github.com/rjzflynnbx/Sitecore-CDP-Scripts/blob/master/_TM%20Script/Sitecore%20CDP%20base%20script.user.js

Instructions:
 1. Copy the code from either file
 2. Create a new tampermonkey script with that code
 3.   Update the [match](https://www.tampermonkey.net/documentation.php#_match) value to target your website.
  4. Inside the script update the  Sitecore client key and pointOfSale (PoS) values to match your Sitecore CDP/P tenant client key and pointofsale.

#### What do these scripts do?

Both scripts:
1. Install the Sitecore CDP/P JS library
2. Send a page VIEW event to Sitecore CDP/P on each page load

[This](https://github.com/rjzflynnbx/tampermonkey-script/blob/main/script.js) one also enables 2 keyboard shorcuts:
1. CTRL+A = start a new anonymous session
2. CTRL+C = close the current session

### Installing a demo bar for a more comprehensive demo

There are 2 'demo bars' that you can use to manually send additional events to Sitecore CDP/P to enhance your demo.

These demo bars allow you to send custom evets, identity events and so on to Sitecore CDP/P.

#### Hidden Demo Bar

Link: [here](https://github.com/rjzflynnbx/tampermonkey-script/tree/main/demos/generic_demo_with_menu).

How it looks: 
![enter image description here](https://i.ibb.co/g3khp68/Screenshot-2022-07-28-at-14-30-16.png)

This TamperMonkey script installs the JS library *and* gives you a demo bar to send additional events.

So if you use this script you do not need to install an additional script to install the Sitecore CDP/P JS library.

The JS installation and demo bar are bundled into this 1 TamperMonkey script.

Update the script match value, client key, and pointOfSale.

To show/hide the hidden demo bar press CTRL + D.

### Demo Bar 2

Link: [here](https://github.com/rjzflynnbx/Sitecore-CDP-Scripts/tree/master/Experiences/Web/Slide%20out%20demo%20bar).

How it looks: 
![enter image description here](https://camo.githubusercontent.com/1118f22c2bd09014b14bee80cb29ddf3338cacbcf77072cf4e2fb9990d099b7d/68747470733a2f2f692e6962622e636f2f73527a66774b4b2f53637265656e73686f742d323032322d30342d30372d61742d31302d35322d31382e706e67)

For this demo bar you need to use a TamperMoney script to install the Sitecore CDP/P JS library on your target website, as described at the beginning of this document.

Once the CDP/P JS library is installed via the tampermonkey script.

You can 'install' this demo bar to send additional events.

This demo bar is "installed" as a Sitecore CDP/P Web Experience.

To install the demo bar follow the instructions [here](https://github.com/rjzflynnbx/Sitecore-CDP-Scripts/tree/master/Experiences/Web).

### Demo bar to display the Guest timeline on your target website

Link: [here](https://github.com/rjzflynnbx/Sitecore-CDP-Scripts/tree/master/Experiences/Web/Slide%20our%20guest%20data%20bar).

How it looks: 
![enter image description here](https://camo.githubusercontent.com/2a55fd4e976f9f300d3d00f186efd536138420f3a0b4e86ab9754d2836e66a4e/68747470733a2f2f692e6962622e636f2f724774723048352f7468756d626e61696c2d696d6167653030332d322e706e67)

To use this demo bar you need to use a TamperMoney script to install the Sitecore CDP/P JS library on your target website, as described at the beginning of this document.

This demo bar is "installed" as a Sitecore CDP/P Web Experience.

To install the demo bar follow the instructions [here](https://github.com/rjzflynnbx/Sitecore-CDP-Scripts/tree/master/Experiences/Web).

## Frequent Problems 

If a script is not loading/working first check your [matcher](https://www.tampermonkey.net/documentation.php#_match) and ensure its working.

Copy the URL directly from the address bar in your browser.

When the matcher is working - on your target website you should see a '1' icon next to the tampermonkey plugin icon that indicates that one script is loaded.

If still not working after you have confirmed the matcher works then open the developer console and look for errors:

 **Content security policy error:**

Install the  [ Allow CORS: Access-Control-Allow-Origin](https://chrome.google.com/webstore/detail/allow-cors-access-control/lhobafahddgcelffkeicbaginigeejlf?hl=en#:~:text=Allow%20CORS%3A%20Access%2DControl%2DAllow%2DOrigin%20lets%20you,default%20(in%20JavaScript%20APIs).) Chrome plugin, configure, and re-try.


 **CORS error:**

Install the  [Disable Content-Security-Policy](https://chrome.google.com/webstore/detail/disable-content-security/ieelmcmcagommplceebfedjlakkhpden?hl=en) Chrome plugin, configure, and re-try.


 **Other problems:**

*Subdomain tracking not working*

Configure the [cookie_domain](https://doc.sitecore.com/cdp/en/developers/sitecore-customer-data-platform--data-model-2-1/javascript-tagging-examples-for-webpages.html) setting in your script
