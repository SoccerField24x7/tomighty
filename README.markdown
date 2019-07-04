# Tomighty is...
==============

A desktop timer app that helps you apply the Pomodoro Technique.
It's written in Java and designed to be simple, easy to use and unintrusive.

Know more about it at [www.tomighty.org](http://www.tomighty.org)

The source code of the Mac version is at https://github.com/ccidral/tomighty-osx

## Notice
------

This branch contains the old source code written in Java which is being discontinued.
The project is being rewritten from scratch in C++ on top of Qt 5. See the `develop`
branch for more information.  _Update: this new C++ build also seems abandoned_

## Building
--------

Regardless of your operating system, you must have the following things installed on it and included in your path:

  * JRE 1.5 or greater
  * Maven 2.x or greater
  * Git

Under Windows platform you also must have:

  * NSIS 2.x or greater

Open a system shell and check out the sources into some directory. Then `cd` into that directory and type:

  `mvn clean package`

The resulting built artifacts will be located under the `target` directory. ~~That's it~~.

## Additional Setup/Info (circa mid 2019)
When I attempted to build this, it hadn't been touched in 5 years, and a lot changes in the tech world in that amount of time!
For example:
* Codehaus was referenced, and they closed up shop back in 2015.
* Some versions of things no longer existed.
* The original SVN repo, gone.
* URLs changed or defunct.
* Etc. etc. etc

I have updated (or ripped out) the dated build directives, so you don't have any action here.

### Things I had to fix in my environment:
Keep in mind that I am not a Java developer by trade so my solutions may not be as elegant as they could be, but here are a few things I had to do to get a new executable:

* Set the `JAVA_HOME` environment variable: `control sysdm.cpl`. Although `javac` was in my path, the build kept complaining that it couldn't find javac in *C:\Program Files\Java\jre1xxx*.  I tried copying it there for grins and giggles, but that wasn't the answer...
** Point `JAVA_HOME` to the root *?\jdk1xxx* directory, not the `?\jdk1xxx\bin\`
** Be sure to close your cmd window, and reopen it after updating environment/path variables.
* I was also getting an error that the Maven executable could not be found.  A helpful Stack Overflow post suggested that I copy bin/mvn.cmd to mvn.bat.  That moved me past that issue.

## Things I didn't Need
* NSIS - I used the `Windows` build profile (more on this later) and was able to generate the executable.  I'm guessing that'll be useful for packing and deployment, but I'll cross that bridge if/when I come to it.
* The `tomighty-swing-0.8.0.jar` without dependencies. I spent a LONG time chasing *JNI error has occurred* before I found I could run the *jar-with-dependencies* version and retargeted launch4j to use it.  (this is probably my lack of Java experience coming into play!)
* There's probably more that I will add here...

## How to get the .EXE
`mvn clean package -PWindows -e`  (leave off the -e if you don't want additional stack trace info when something fails)

## Why am I updating this?
I am a fan of the Pomodoro technique, and this implementation is simple and powerful (at least to my way of thinking!). The thing I really wished this would give me is
some history. How many have I earned?  What's my trend?  One of the existing enhancement requests asked for holding your count for the day on logout. So, here I am to:
a) get the features I want
b) learn something
c) give back (in the event someone out there loves this timer as much as I do)

