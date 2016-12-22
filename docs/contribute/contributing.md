# Contributing

So you'd like to contribute? Wonderful! Opensource projects like these are driven by volunteers, so the more, the merrier.

If you haven't done so already, head over to the [Development Environments](development-environments) wiki page.  That page will walk you through the steps to get the code and set up a development environment.

## Not a coder? ##

That's not a problem.  There are several ways you can help still
* Join the [forum](https://forum.dronin.org/) and [IRC](http://kiwiirc.com/client/irc.kiwiirc.com/dronin/) to help out other users
* Contribute to the documentation on the wiki
* [[Help test new code|Reviews-needing-flight-testing]]

## Contacting the developers? ##

The developers can be found in two main places:
* The [dRonin forum](https://forum.dronin.org)
* The [#dronin chat channel](http://kiwiirc.com/client/irc.kiwiirc.com/dronin/) on freenode.net

## Looking for something to work on? ##

If you have your own idea that you want to explore, great! But if you'd like to look a list of issues that are already opened, we have helpfully labeled tasks that we think are good for getting familiar with the code. Just look for the "difficulty/low" tag in the [list of open issues](https://github.com/d-ronin/dronin/issues?sort=created&state=open).

## Found a bug? ##

First, check if the issue you've found has already been reported:
* Search the [list of open issues](https://github.com/d-ronin/dronin/issues?sort=created&state=open).
* Search the [dRonin](https://forum.dronin.org) google group for any open discussion on the issue.

If you don't see the issue in any of those places, head over the the [issue tracker](https://github.com/d-ronin/dronin/issues?sort=created&state=open) and write up your bug report.

If you're also planning on contributing a fix for this issue, mention that in your bug report so that we know you're working on it.

It's always best to briefly describe how you plan to fix the issue as a reply to the bug report and then to check back often to see if the developers have provided any suggestions for you.

## Want to add a new feature? ##

If you have your own idea that you want to explore, great!

Before you get started, you'll want to find out if anyone else is already working on something similar (or identical!).  If this feature has been requested already, there might also be some good discussion about how to get it done.
* Search the [list of open issues](https://github.com/d-ronin/dronin/issues?sort=created&state=open).
* Search the [dRonin](https://groups.google.com/forum/#!forum/dronin) google group for any open discussion on the feature.

If you don't see any sign of the feature you want to add in any of those places, you should start a discussion thread in the [dRonin](https://groups.google.com/forum/#!forum/dronin) google group describing your feature as clearly as possible.  This thread will be the place where other users and developers can help you work out some of the details about how best to implement the feature.  Once some of the details have been worked out, you can get started with the code.

When adding your first feature to the code base, you might want to ask if one of the developers is available to mentor you through the process.  It's not that difficult but you might find it easier with a guide for the first time.

If you're stuck at any point, **please** don't hesitate to ask for some help.

# Submitting your code #

Once you're done with your bug-fix or feature, the last step is submitting a pull request. This is as easy as [clicking a button](https://help.github.com/articles/creating-a-pull-request). Once your pull request is started, the continuous integration server (Jenkins) will automatically start to compile the new code, making sure that it builds for all targets. If everything is okay, then Jenkins will report that the build succeeded. If not, then Jenkins will report back with an error, visible on the Github pull request page, like shown:
[[http://i.imgur.com/OOb5Zue.png|alt=Jenkins Results]]

Clicking the "Details" link will take you to the Jenkins build. Click "Console Output" on the left menu to see full build output. Tip: Ctrl+F and search for "error".

After submitting your pull request, dRonin developers will be informed that a pull has been requested and they will review your code.  Please be patient during this stage since proper code reviews take time.  You should also be prepared to address any feedback that you get during the code review.  Once you've fixed any issues identified during review, your code will be merged into the upstream `next` branch which is where the active development lands.

Please see these notes for [[Development-Coding-standards]] to make sure your new features are incorporated as quickly as possible.

# Notes for various parts of the code

* [[Math Libraries|math]]
