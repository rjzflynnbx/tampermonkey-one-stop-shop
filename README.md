# Tampermonkey "One-Stop-Shop"


On this page you will find all of the information you need to know about how to use [TamperMonkey](https://www.tampermonkey.net/) to create a custom Sitecore CDP/P demo.


## What is a "tampermonkey demo"?

This kind of custom demo allows you to:
 1. Show data capture in Sitecore CDP/P on any website
 2. Publish Sitecore Personalize Experiences on any website

## Installing Tampermonkey

[Tampermonkey](https://www.tampermonkey.net/) is a browser (Chrome, Firefox etc.) plugin. Just check their docs or Google or Youtube to figure out how to install the plugin.

## Installing the Sitecore CDP/P JS library on a website with Tampermonkey

Go [here](https://github.com/Chris-Castle/Sitecore-CDP-Scripts) for instructions.

## Frequent Problems 

If a script is not loading/working first check your [matcher](https://www.tampermonkey.net/documentation.php#_match) and ensure its working.

Copy the URL directly from the address bar in your browser.

When the matcher is working - on your target website you should see a '1' icon (at least 1, maybe more) next to the tampermonkey plugin icon that indicates that one script is loaded.

If still not working after you have confirmed the matcher works then open the JavaScript console and look for errors:

 **Content security policy error:**

Install the  [ Allow CORS: Access-Control-Allow-Origin](https://chrome.google.com/webstore/detail/allow-cors-access-control/lhobafahddgcelffkeicbaginigeejlf?hl=en#:~:text=Allow%20CORS%3A%20Access%2DControl%2DAllow%2DOrigin%20lets%20you,default%20(in%20JavaScript%20APIs).) Chrome plugin, configure, and re-try.


 **CORS error:**

Install the  [Disable Content-Security-Policy](https://chrome.google.com/webstore/detail/disable-content-security/ieelmcmcagommplceebfedjlakkhpden?hl=en) Chrome plugin, configure, and re-try.


**Subdomain tracking not working**



Configure the [cookie_domain](https://doc.sitecore.com/cdp/en/developers/sitecore-customer-data-platform--data-model-2-1/javascript-tagging-examples-for-webpages.html) setting in your script

**Page views not triggering, website is a SPA/React/Angular etc. app**


Add the following code to the tampermonkeys script

        let lastUrl = location.href;
    new MutationObserver(() => {
        const url = location.href;
        if (url !== lastUrl) {
            lastUrl = url;
            onUrlChange();
        }
    }).observe(document, { subtree: true, childList: true });
    
    function onUrlChange() {
        delayUntilBrowserIdIsAvailable(sendViewEvent);
    }

Here's how you can place the code:

![enter image description here](https://github.com/rjzflynnbx/tampermonkey-one-stop-shop/assets/57630487/4b52e590-7a20-4d48-9d41-2f5efefd4dc5)
