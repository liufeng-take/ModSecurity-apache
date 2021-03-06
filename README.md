
<img src="https://github.com/SpiderLabs/ModSecurity/raw/v3/master/others/modsec.png" width="50%">

[![Build Status](https://travis-ci.org/SpiderLabs/ModSecurity-apache.svg?branch=master)](https://travis-ci.org/SpiderLabs/ModSecurity-apache)
[![](https://raw.githubusercontent.com/ZenHubIO/support/master/zenhub-badge.png)](https://zenhub.com)


The ModSecurity-apache connector is the connection point between Apache and libmodsecurity (ModSecurity v3). Said another way, this project provides a communication channel between Apache and libmodsecurity. This connector is required to use LibModSecurity with Apache. 

The ModSecurity-apache connector takes the form of an Apache module. The module simply serves as a layer of communication between Apache and ModSecurity.

Notice that this project depends on libmodsecurity rather than ModSecurity (version 2.9 or less).


### What is the difference between this project and the old ModSecurity module for Apache?

The old version of ModSecurity was origionally designed for and contained within an Apache module. This current version abstracts out some of the details allowing ModSecurity to more easily support multiple platforms and features outside beyond the scope of what Apache internals currently support. As a result using the new libmodsecurity engine is no longer reliant on the use of Apache and can be used to power multiple different connectors. As a result of this the current version is more flexible, has wider support, and allows for the support of new functionality that was not previously possible.


# Compilation

Before compile this software make sure that you have libmodsecurity installed.
You can download it from the ModSecurity git repository. For information pertaining to the compilation and installation of libmodsecurity please consult the documentation provided along with it.

With libmodsecurity installed, you can proceed with the installation of the ModSecurity-apache connector. Run the following commands:

```
$ ./autogen.sh
$ ./configure
$ make
$ sudo make install
```

# Contributing

As an open source project we invite (and encourage) anyone from the community to contribute to our project. This may take the form of: new
functionality, bug fixes, bug reports, beginners user support, and anything else that you
are willing to help with. Thank you.

## Providing Patches

We prefer to have your patch within the GtiHub infrastructure to facilitate our
review work, and our QA integration. GitHub provides an excellent
documentation on how to perform “Pull Requests”. More information available
here: https://help.github.com/articles/using-pull-requests/

Please respect the coding style. Pull requests can include various commits, so provide one fix or one piece of functionality per commit. Please do not change anything outside the scope of your target work (e.g. coding style in a function that you have passed by). For further information about the coding style used in this project, please check: https://www.chromium.org/blink/coding-style

Please respect the coding style in use. Pull requests can include various commits, so
provide one fix or one functionality per commit. Do not change anything outside
the scope of your target work (e.g. coding style in a function that you have
passed by). 

### Don’t know where to start?

Within our code there are various items marked as TODO or FIXME that may need
your attention. Check the list of items by performing a grep:

```
$ cd /path/to/modsecurity-apache
$ egrep -Rin "TODO|FIXME" -R *
```

You may also take a look at recent bug reports and open issues to get an idea of what kind of help we are looking for.

### Testing your patch

Along with the manual testing, we strongly recommend that you to use the Apache test
utility to make sure that you patch does not adversly affect the behavior or performance of Apache. 

The Apache testing tools are available on: http://httpd.apache.org/test/

To use those tests ....
 #TODO#

If you are facing problems getting your added functionality to pass all the  Apache tests, feel free to contact us or the Apache mailing list at: http://httpd.apache.org/lists.html

### Debugging 
Because the ModSecurity Apache Connector runs as part of Apache, one needs to debug the Apache process. Debugging may require several steps. In general debugging can be enabled by compiling the Apache connector with debugging as follows:
```CFLAGS="-g -O0" ./configure ...normal configure parameters...)```

It is recommended that one keeps the debugging process as simple as possible, to do so, the elimination of features such as multi-threading by the HTTP server is recommended. A special "--with-debug" option can also be used during the compilation of the Apache Connector that will enable the connector's debug messages.

Apache webservers accept a special command line parameter: "-X", that starts the server in debug mode and doesn't detach it from the console. This flag should be passed straight to the apache2 or httpd binary, along with any other options, such as the configuration file that should be used. The parameter should not be passed to the apachectl script, instead, the http/apache2 file should be used directly. If you are using Ubuntu your Apache will probably be at: /usr/sbin/apache2. If you are using Fedora this will probably be at: /usr/sbin/httpd.

This setup may affect the behavior of the HTTP server in a way that makes impossible or more difficult to reproduce a given bug, if this is the case, you may wish to ask for help in our mailing list and check out Apache's debugging instructions at: https://httpd.apache.org/dev/debugging.html.

## Reporting Issues

If you are facing a configuration issue or if something is not working as you
expect it to be, please use ModSecurity user’s mailing list. Issues on GitHub
are also welcome, but we prefer to have users question on the mailing list first,
where you can reach an entire community. Also don’t forget to look for an
existing issue before opening a new one.

Lastly, If you are planning to open an issue on GitHub, please don’t forget to tell us the
version of your libmodsecurity and the version of the Apache connector you are running.

### Security issue

Please do not publicly report any security issue. Instead, contact us at:
security@modsecurity.org to report the issue. Once the problem is fixed we will provide you with credit for the discovery.

## Feature Request

We would love to discuss any ideas that you may have for a new feature. Please keep in mind this is a community driven project so be sure to contact the community via the mailing list to get feedback first. Alternativly, feel free to open GitHub issues requesting for new features. Before opening a new issue, please check if there is an existing feature request for the desired functionalityt.

## Packing

Having our packages in distros on time is something we highly desire. Let us know if
there is anything we can do to facilitate your work as a packager.
