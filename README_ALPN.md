## This is a private patch to support ALPN in Node.js ##

Caution: this works only on Linux

### How to build. ###

- Obtain the repository and update openssl submodule
````
 git clone https://github.com/shigeki/node alpn_support

 git submodule init deps/openssl

 git submodule update deps/openssl
````

- Build openssl

````

cd deps/openssl

./config

make depend

make

````

- check if libcrypto.a and libssl.a exist in deps/openssl/

- Build Node.js

````

./configure

make

````

- check openssl version in Node


````

> ./node -e 'console.log(process.versions.openssl)'

1.1.0-dev

````

### How to set NPN ###

specify options.ALPNProtocols as the same way of NPNProtocols in server and connection.

please refer test/simple/test-tls-alpn-server-client.js
