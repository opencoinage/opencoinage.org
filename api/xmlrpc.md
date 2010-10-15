XML-RPC Application Programming Interface (API) {#top}
===============================================

This document describes and specifies an XML-RPC protocol for OpenCoinage
operations.

[TOC]

Overview
--------

[XML-RPC][] is a remote procedure call (RPC) protocol that uses [XML][] to
encode method calls and [HTTP][] as the transport mechanism. To the extent
that anything XML-based can be called lightweight and straightforward,
XML-RPC is lightweight and straightforward. More importantly than that, it
is ubiquitous: mature XML-RPC client libraries are available for every
popular programming language.

Endpoint
--------

TODO

Authentication
--------------

Authentication is orthogonal to XML-RPC. Standard HTTP [basic][] or
[digest][] authentication mechanisms may be used as needed.

[basic]:  http://en.wikipedia.org/wiki/Basic_access_authentication
[digest]: http://en.wikipedia.org/wiki/Digest_access_authentication

Methods
-------

### opencoinage.version {#version}

TODO

#### Request {#version-request}

    POST /xmlrpc HTTP/1.1
    Host: localhost
    User-Agent: Drupal
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...

    <?xml version="1.0"?>
    <methodCall>
      <methodName>opencoinage.version</methodName>
    </methodCall>

#### Response {#version-response}

    HTTP/1.1 200 OK
    Connection: close
    Date: ...
    Server: ...
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...
    
    <?xml version="1.0"?>
    <methodResponse>
      <params>
        <param>
          <value>0.0.0</value>
        </param>
      </params>
    </methodResponse>

### opencoinage.verify {#verify}

TODO

#### Request {#verify-request}

    POST /xmlrpc HTTP/1.1
    Host: localhost
    User-Agent: Drupal
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...
    
    <?xml version="1.0"?>
    <methodCall>
      <methodName>opencoinage.verify</methodName>
      <params>
        <param>
          <value>...</value>
        </param>
      </params>
    </methodCall>

#### Response {#verify-response}

### opencoinage.describe {#describe}

TODO

#### Request {#describe-request}

    POST /xmlrpc HTTP/1.1
    Host: localhost
    User-Agent: Drupal
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...
    
    <?xml version="1.0"?>
    <methodCall>
      <methodName>opencoinage.describe</methodName>
      <params>
        <param>
          <value>...</value>
        </param>
      </params>
    </methodCall>

#### Response {#describe-response}

### opencoinage.reissue {#reissue}

TODO

#### Request {#reissue-request}

    POST /xmlrpc HTTP/1.1
    Host: localhost
    User-Agent: Drupal
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...

    <?xml version="1.0"?>
    <methodCall>
      <methodName>opencoinage.reissue</methodName>
      <params>
        <param>
          <value>...</value>
        </param>
      </params>
    </methodCall>

#### Response {#reissue-response}

### opencoinage.merge {#merge}

TODO

#### Request {#merge-request}

    POST /xmlrpc HTTP/1.1
    Host: localhost
    User-Agent: Drupal
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...

    <?xml version="1.0"?>
    <methodCall>
      <methodName>opencoinage.merge</methodName>
      <params>
        <param>
          <value>...</value>
        </param>
      </params>
    </methodCall>

#### Response {#merge-response}

### opencoinage.split {#split}

TODO

#### Request {#split-request}

    POST /xmlrpc HTTP/1.1
    Host: localhost
    User-Agent: Drupal
    Content-Type: text/xml; charset=UTF-8
    Content-Length: ...

    <?xml version="1.0"?>
    <methodCall>
      <methodName>opencoinage.split</methodName>
      <params>
        <param>
          <value>...</value>
        </param>
      </params>
    </methodCall>

#### Response {#split-response}

Data Types
----------

### Tokens

TODO

Error Codes
-----------

TODO

History
-------

* **2010/09/01** Initial draft of specification.

License
-------

This specification is in the public domain. In jurisdictions that recognize
copyright laws, you may apply the [Creative Commons Zero][CC-Zero] license.

[XML-RPC]:      http://en.wikipedia.org/wiki/XML-RPC
[XML-RPC spec]: http://www.xmlrpc.com/spec
[XML-RPC FCI]:  http://xmlrpc-epi.sourceforge.net/specs/rfc.fault_codes.php
[XMPP-RPC]:     http://xmpp.org/extensions/xep-0009.html
[XML]:          http://en.wikipedia.org/wiki/XML
[HTTP]:         http://en.wikipedia.org/wiki/HTTP
[XMPP]:         http://en.wikipedia.org/wiki/XMPP
[CC-Zero]:      http://creativecommons.org/publicdomain/zero/1.0/
