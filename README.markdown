openssl-xcode
=============

This is an XCode project skeleton structure that can be used to build a static 
libcrypto.a and libssl.a libraries for use in MacOS and iOS/tvOS projects. 

This project was forked from [michaeltyson/openssl-xcode](https://github.com/michaeltyson/openssl-xcode) and specifically updated to target 64-bit architectures [x86_64, ARM64] and combination 64-bit/32-bit universal builds to generate static OpenSSL libraries against XCode toolchain build tools circa OSX 10.14 and iOS 12.2 with compatibility as far back as 10.6 and 8.0 respectively.  It has successfully generated x86_64 and arm64 static openssl libs against the latest git pull of OpenSSL 3.0.0 -- but these generated libs have not been tested just yet.  

The remainder of the README was composed by and forked from Michael Tyson's branch:

Usage
-----

In a normal case you would use it thusly:

1. Download the OpenSSL source code directly from
   http://www.openssl.org/source/ 
2. Clone the openssl-xcode git repo to make a local copy
3. Put the downloaded OpenSSL source tar.gz into the same folder
   as openssl.xcodeproj.  
   The extracted OpenSSL distribution can also be placed in a folder called 'openssl'
   within the same folder as openssl.xcodeproj, or just extracted within the
   same folder as openssl.xcodeproj.

Then, either open openssl.xcodeproj in XCode and initiate a build, or integrate
it within another project:

1. Drag the openssl.xcodeproj file into your main project
2. Right-click on your project target, and add openssl.xcodeproj under "Direct
   Dependencies" on the General tab.
3. On the Build tab for your project's target, find the "Header Search Paths" 
   option, and add the path:
   > `$(SRCROOT)/Library/openssl/build/openssl.build/openssl/include`
   
   (Assuming you've put openssl.xcodeproj at the path Library/openssl, and are
   building from a source tarball)
4. Expand your target's "Link Binary With Libraries" build stage, and drag
   libcrypto.a from the openssl.xcodeproj group.


This project actually relies on the OpenSSL configure and make
system to build the libraries. However, it does attempt to automatically
detect and use the appropriate build settings for arch (i386/ppc/armv6),
build tools, and SDK directories. This makes it appropriate for inclusion
as a project reference into an iPhone application project.

License
-------

Copyright (c) 2009, ZETETIC LLC
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright
  notice, this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright
  notice, this list of conditions and the following disclaimer in the
  documentation and/or other materials provided with the distribution.
* Neither the name of the ZETETIC LLC nor the
  names of its contributors may be used to endorse or promote products
  derived from this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY ZETETIC LLC ''AS IS'' AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL ZETETIC LLC BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

