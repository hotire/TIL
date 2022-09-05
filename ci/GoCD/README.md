# GoCD

https://www.gocd.org/


## install mac 

https://docs.gocd.org/current/installation/install/server/osx.html


Download the Mac OS X installer for GoCD Server from downloads page.

Unzip the installer in a directory of your choice. It creates a sub-directory with the name go-server-${version}.

Mark the directory as not quarantined by Mac OS X so that it allows the GoCD Server to be started:

~~~
# Assuming, for example, that the directory is "go-server-20.5.0".
$ cd go-server-20.5.0
$ xattr -d -r com.apple.quarantine .
xattr: [Errno 13] Permission denied: './jre/Contents/Home/lib/server/classes.jsa'
xattr: [Errno 13] Permission denied: './jre/Contents/Home/legal/jdk.dynalink/dynalink.md'
... # These "Permission denied" warnings can be ignored.
~~~
