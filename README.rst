Description
===========
This is just a website image scrapper. It does only that. No fancy code or
anything.

If you're fan of some hentai artists and you would like to have all their
iamges, just employ this script and there you have it.

It will not filter anything. It will use wget to download all the image and swf
files in the website. No special filtering (yet) nor auto-discovery (yet).

Usage
=====

First, go to a webiste and analize it. See which files you'd like and where
those files are stored. Make sure to select the author's images. For example, 
there are a lot of authors using blogs these days. These blogs use:

    image-server-42-bla.fc4.jp (or something)

    image-server-44-bla.fc4.jp
    
    image-server-12-bla.fc4.jp

So, if this is the case, just modify the getme script so it meets your
requirements. 

Some other authors have 2 or three websites and include files from them all.
This is simple, just add those websites to the $urls variable.

    urls="${url},site1.otaku.tw,site2.hentaihost.ch,mypersonalsite.blogbla.org"

As you can see, the urls var includes the url var (the main website url) so no
need to add it again.

IMHO, it's very straight forward and you will get the hang of
it... if you still use your brain...


Example
=======

Now a working example:

Let's say that you want to backup WarsWarz website so, if he looses his files,
you can provide them to him ;)

You go to his website and notice that he uses 2 domains for his files:
    
    - http://www2.ocn.ne.jp/~warz/Graphs.html
    - http://warzwars.ifdef.jp/Graphs.html

So, now, you need to configure your getme file:

    cp getme ~/hentai/websites/WarsWarz/.getme

    gedit ~/hentai/websites/WarsWarz/.getme

And you would leave it like this:

-- start of ~/hentai/websites/WarsWarz/.getme --

    #!/bin/bash
    # GetMe file
    # this file configures your site.
    #
    # 1. copy this file to /path/to/your/websites/images/dir/.getme
    # 2. make sure the configuration is ok
    # 3. run getImages pointing to where your website directories are
    #    ej. getImages /path/to/your/websites/

    # getImages vars
    #

    # main url
    
    url="http://www2.ocn.ne.jp/~warz/Graphs.html http://warzwars.ifdef.jp/Graphs.html"

    # possible image servers (csv urls)
    
    urls="$url,www2.ocn.ne.jp,warzwars.ifdef.jp"

    # user agent to use
    
    userAgent="Mozilla/5.0 (X11; U; Linux x86_64; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.70 Safari/533.4"

    # file types (csv)
    
    types="bmp,gif,jpeg,jpg,png,svg,tiff,swf"

-- end of  ~/hentai/websites/WarsWarz/.getme --

and, now, just run getImages
    
    bash getImages ~/hentai/websites

GetImages will find all the .getme files and start downloading stuff it finds
there. It will leave a log file too, so you know what happened.

Feel free to play with the .getme script to get the results you want.


Disclaimer
==========

This script has no warranty of any kind. The images of the authors are their own
property and should be used only in ways authorized by them.

This script doesn't work with image sites like deviantart.com and stuff like
that. It is not recommended to use it with them.
