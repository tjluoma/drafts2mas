drafts2mas
==========

Use Drafts.app (iOS), Hazel (Mac), and Dropbox to view Mac App Store app information on an iOS device

# The Problem:

You are on your iPhone or iPad and you hear about this cool new Mac App Store app, so you google it, click the link… and find yourself staring at a page that tells you that you can only see Mac App Store apps on a Mac.

*Or* you're on your iPhone and hear about a cool new iPad app, but it's iPad-only, and so you can't see anything about it either.


## The Solution:

Take that link, put it into Drafts.app on your iOS device, save it to Dropbox. Meanwhile on your Mac, Hazel sees a file, processes it, and creates a web page that you *can* view on your iOS device. 


## Warning!

This project assumes that you are comfortable with the command-line. If you aren't, it's probably not for you. This isn't a "drop in" solution, you'll have to do some of the work yourself.

## What you'll need 

* [Hazel](http://www.noodlesoft.com/hazel) running on a Mac which is always on and connected to your Dropbox account. (Yeah, FolderActions or launchd should work, but Hazel is more reliable and easier.)

* An iOS device running the awesometacular
 [Drafts for iOS](https://itunes.apple.com/us/app/drafts/id502385074?mt=8).

* Click on <a href="drafts://x-callback-url/import_action?type=dropbox&name=MAS-urls.txt&path=%2FApps%2FDrafts%2FMAS%2F&filenametype=0&filename=&ext=txt&writetype=0&template=%5B%5Bdraft%5D%5D">this Drafts Action</a> on your iOS device, which will install the action on your device.

* move 'mas-makepage.sh' to /usr/local/bin/mas-makepage.sh

* Make this directory in Finder: **"~/Dropbox/Apps/Drafts/MAS/""** (where ~ is your HOME directory).

* Add **"~/Dropbox/Apps/Drafts/MAS/"** to Hazel.

* Download [MAS.hazelrules][] and import it into Hazel

* Install `multimarkdown` and `lynx` (I recommend [Homebrew](http://mxcl.github.com/homebrew/).)

* Install `html2text.py` from <https://github.com/aaronsw/html2text/downloads>

* move basic-clean-reformat.rc to /usr/local/etc/tidy/basic-clean-reformat.rc

* You'll need to make a file `textme.sh` that sends you the URL when the file is uploaded. I recommend using [voicesms.rb](http://brettterpstra.com/2010/11/19/sms-from-the-command-line-with-google-voice/) with Google Voice. ***But that part is up to you.***

[MAS.hazelrules]: MAS.hazelrules

## Where do you want the files to go?

You'll need some sort of a webserver to display these pages. I recommend setting up a free [site44](http://www.site44.com) account. Then you can upload files to your website just by putting them into a folder in Dropbox.

You could also `scp` the file to a server if you already have one. You'll see where in the `mas-makepage.sh` file.

## There is an alternative!

If you'd rather get the files sent to you via email instead of uploading them to a website, see <https://github.com/tjluoma/appstorebyemail> which does something similar but via email.
