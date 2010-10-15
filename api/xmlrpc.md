XML-RPC Application Programming Interface (API)
===============================================

This document describes and specifies an XML-RPC protocol for OpenCoinage
issuance operations.

[TOC]

Overview
--------

[XML-RPC][] is a remote procedure call (RPC) protocol that uses [XML][] to
encode method calls and [HTTP][] or [XMPP][] as the transport mechanism. To
the extent that anything XML-based can be called lightweight and
straightforward, XML-RPC is lightweight and straightforward. More
importantly than that, it is ubiquitous: mature XML-RPC client libraries are
available for every popular programming language.

Transports
----------

XML-RPC in and of itself is merely a method of encoding RPC requests and
responses in XML. XML-RPC payloads can be transmitted over a variety of
transports; at present, HTTP and XMPP are well-defined and in wide use.

### HTTP

[HTTP][] is the standard transport for XML-RPC payloads.

### XMPP

[XMPP][] can be used as the transport as defined in [XEP-0009][XMPP-RPC].

Endpoint
--------

TODO

Authentication
--------------

Authentication is orthogonal to XML-RPC. When using HTTP as the transport,
standard HTTP [basic][] or [digest][] authentication mechanisms may be used
as needed.

[basic]:  http://en.wikipedia.org/wiki/Basic_access_authentication
[digest]: http://en.wikipedia.org/wiki/Digest_access_authentication

Methods
-------

### opencoinage.version {#version}

Returns the server's version number.

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
          <value><string>0.0.1</string></value>
        </param>
      </params>
    </methodResponse>

### opencoinage.verify {#verify}

Returns `true` if the given token is valid, and `false` otherwise.

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
          <value>
            <string>fQHFukq179n50tC7q3LQqlY9SJn5m2WNoxdylekZJU5SfxNzWSRKA8H5jK054gUNnMTOSVWDwUGFc6ZnC0IdAF</string>
          </value>
        </param>
      </params>
    </methodCall>

#### Response {#verify-response}

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
          <value><boolean>1</boolean></value>
        </param>
      </params>
    </methodResponse>

### opencoinage.describe {#describe}

Returns information about the given token.

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
          <value>
            <string>fQHFukq179n50tC7q3LQqlY9SJn5m2WNoxdylekZJU5SfxNzWSRKA8H5jK054gUNnMTOSVWDwUGFc6ZnC0IdAF</string>
          </value>
        </param>
      </params>
    </methodCall>

#### Response {#describe-response}

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
          <value>
            <struct>
              <member>
                <name>valid</name>
                <value>
                  <boolean>1</boolean>
                </value>
              </member>
              <member>
                <name>issuer</name>
                <value>
                  <string>http://example.org/</string>
                </value>
              </member>
              <member>
                <name>currency</name>
                <value>
                  <string>http://example.org/monopoly-dollar</string>
                </value>
              </member>
              <member>
                <name>amount</name>
                <value>
                  <string>0.25</string>
                </value>
              </member>
              <member>
                <name>expires</name>
                <value>
                  <dateTime.iso8601>2010-12-31T23:59:59Z</dateTime.iso8601>
                </value>
              </member>
            </struct>
          </value>
        </param>
      </params>
    </methodResponse>

### opencoinage.reissue {#reissue}

Issues a new token equivalent to the given token.

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
          <value>
            <string>fQHFukq179n50tC7q3LQqlY9SJn5m2WNoxdylekZJU5SfxNzWSRKA8H5jK054gUNnMTOSVWDwUGFc6ZnC0IdAF</string>
          </value>
        </param>
      </params>
    </methodCall>

#### Response {#reissue-response}

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
          <value>
            <string>n9ZF9jUBFLf6GITN4l0TPq8tT3Jxl9WSZ3drv3xNtCZQWVhuyrWonOK9gMhwChj8fYkmFQU7yXZ0KFmsA2fqsF</string>
          </value>
        </param>
      </params>
    </methodResponse>

### opencoinage.merge {#merge}

_Not yet specified._

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
          <value>
            <string>4eVsjWo1xuMSosOuhp6fG50b2cLbgzOo7biundzt8VKXrqZ03NAEJgXe3Yx4HOx7R9KdOsN04oKbDJKYdHfMHJ</string>
          </value>
        </param>
        <param>
          <value>
            <string>itwByCDIgIxlCWwnMk1bYFzMSpRLFyz0ZgOj59eaCk3lZ0UxhdBMVwzFUwqgZ7OQuHomCE5SRPMtmQ5aAeaiTY</string>
          </value>
        </param>
      </params>
    </methodCall>

#### Response {#merge-response}

### opencoinage.split {#split}

_Not yet specified._

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

The protocol defined here makes use of the [XML-RPC FCI][] fault codes.

History
-------

* **2010/10/14** Initial draft of specification.

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
