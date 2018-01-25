
Nginx Auto Lib Module
=====================

New Repo Location
=================

The new location for this repo is :

https://github.com/simplresty/ngx_auto_lib

This old location was :

https://github.com/simpl/ngx_auto_lib

This is one of a number of Nginx modules that have been moved from 'simpl' to 'simplresty'.
See [below](#see-also) for more information on how these organizations are now used.

To prevent any problems with updates, all repos that were previously under the 'simpl' user
will be forked and synced from the 'simplresty' repo. Sorry for any inconvenience this causes.

Description
===========

This module searches for compiled versions of OpenSSL (including MD5 and SHA1),
PCRE and Zlib so that if they are required for an Nginx compilation and compiled
versions are available, then the pre-compiled versions are used rather than
re-compiling new ones each time Nginx is built.

It also has a highly flexible and extensible system for searching for libraries,
which can include both source and installation directories. This can make the
overall process of including external libraries in Nginx compilations easier,
especially when custom compilations of libraries are used.


Installation
============

The module can be added like any other, but it MUST BE THE LAST ADDON MODULE,
since it checks values set by other modules to determine whether or not libraries
are required.

[set variables if desired]
./configure [other config options] --add-module=/path/to/ngx_auto_lib



Setting variables to control where libraries are found
======================================================

Auto Lib has a more flexible configuration system for determining where libraries
are found than the core Nginx distribution. See README_AUTO_LIB under the user
section for more details.

In that file :

PFX ::= MD5 | OPENSSL | PCRE | SHA1 | ZLIB



Notes for module developers
===========================

The majority of the work done by this module is in the ngx_auto_lib_core file,
which is a generic library handler for Nginx modules. Any module developers that
require external libraries for their modules are encouraged to include this file
in their module's config file rather than defining their own config files from
scratch. Even if you have already written config files that include searches for
libraries, you are encouraged to include this file to replace your existing
implementation because it will likely provide more flexibility to the end user
and may be more robust.

See the developers section of the README_AUTO_LIB for more details.



Known issues
============

- does not work correctly with paths that include spaces
- incomplete documentation


To do
=====

- check that reordering of mail modules in OpenSSL config file does not cause problems



License
=======

    BSD


Copright
========

    2010 (c) Marcus Clyne


See Also
========

* **[SimplResty](https://github.com/simplresty)** : A web-application framework integrating 
OpenResty, Couchbase, React and much more
* **[Simpl](https://github.com/simpl)** : A shell platform that integrates repositories stored 
on Github, Bitbucket etc., to help facilitate shell-based tasks
