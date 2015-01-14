---
layout: page
title: Prelaunch
permalink: /prelaunch/
---


Code should be valid and render in browsers bug free. For older browsers the content should still be readable even if the styles don't display 100% correctly. 

Colours and buttons should be readable as per usibility standards for the project.

SEO depends highy on speeds and the correct format of the HTML document. Check these using tools like Yslow and pagespeed insights.

To cover mobile devices and slow connections all assets should be as minimal as possible and any extra content should be loaded lazily or asynchronously. 


##Validation

###HTML

- [http://validator.w3.org/](http://validator.w3.org/)

###CSS


##Browser Testing

- ie 9+ - [Remote test ie](http://blogs.msdn.com/b/ie/archive/2014/11/02/announcing-remoteie-test-the-latest-ie-on-windows-mac-os-x-ios-and-android.aspx)
- Firefox
- Chrome
- Safari
- Opera

##Device testing

###iOS devices

###Android devices

###Windows phone devices


##Usability testing

- Make sure the page is usable for all users (e.g. visual contract and alt tags) [http://achecker.ca/checker/index.php](http://achecker.ca/checker/index.php)
- Check the pages using a bookmarklet - [http://squizlabs.github.io/HTML_CodeSniffer/](http://squizlabs.github.io/HTML_CodeSniffer/)

##Optimization

###Workflow

- CDN hosted assets which are GZipped
- Progressive jpgs and pngs are crushed to a suitable level.
- With expires set a good long time into the future.
- Minified, linted and concatenated js and css where possible for minimal requests
- [DNS prefetching](http://www.htmlgoodies.com/beyond/webmaster/how-your-browser-speeds-up-cross-domain-loading-using-dns-prefetching.html)
- Lazy loading of images to reduce initial page weight
- Inline javascript in header if small enough
- Cache template fragments and database as much as possible for as long as possible (e.g. using memcached etc.)


###Tests and services

####Speed & quality tests

- [http://yslow.org/](http://yslow.org/) - Get a high score on YSlow: 
- [https://developers.google.com/speed/pagespeed/insights/](https://developers.google.com/speed/pagespeed/insights/) - Get a high score on Pagespeed Insights. You need to be aiming for 90+.
- [http://www.webpagetest.org/](http://www.webpagetest.org/) - Get all A’s or B’s on Web page test:
- [http://tools.pingdom.com/fpt/](http://tools.pingdom.com/fpt/) - Get a high score on Pingdom:

##SEO

- [http://www.woorank.com/](http://www.woorank.com/) - Rate site on useful SEO metrics **PAID**
- [http://www.seowebpageanalyzer.com/](http://www.seowebpageanalyzer.com/) - Covers the basic areas of SEO.
- [http://nibbler.silktide.com/](http://nibbler.silktide.com/) - Get high score on Nibler. This is great for giving a good overview to aspects such as code and social recognition, along side other wider ranged metrics.

##Other
