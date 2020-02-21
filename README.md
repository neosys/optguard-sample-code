# optguard-sample-code

Some example code in PHP and Javascript (JS) to demonstrate the integration of the optGuard API. 

There are two ways to integrate:

<b>Method 1:</b> Include the PHP code into a PHP website template (RECOMMENDED).
One should choose this method, if their website supports PHP and can include our few lines of PHP code on landing pages to protect.

<b>Method 2:</b> Embed a JS script in every page of the website. The script will proxy for the PHP script by calling it in a JS script tag. 
As an alternative to method 1, a JS script solution will work on static HTML pages. It will "proxy" the PHP script by calling it as the remote target of the JS event (obviously, the configured PHP script must be hosted SOMEWHERE that supports PHP). Note that this is also a good way to protect a network of sites that all share a single, configured PHP file.

Since bots tend <b><i>not</i></b> to run Javascript (JS), one could argue that relying on a JS script solution would miss the majority of the bots. However, the bots <b><i>we</i></b> want to catch must support JS in order to fraudulently click advertisements. So, for our purposes, we can assume that JS is supported by all visitors we care about. 

However, method 2 is the only solution for websites that cannot include our PHP script (such as with static HTML pages or some types of PHP, opCode, or CDN caching). 


<b>PHP Script Purpose:</b> Once executed, our code will pull the visitor's IP via the web server and PHP framework. This simple script will pass along the IP address of the visitor to our API, using the configured access and secret keys. 
