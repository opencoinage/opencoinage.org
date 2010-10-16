Python Software Development Kit (SDK)
=====================================

TODO

Classes
-------

* [`opencoinage.Issuer`][Issuer]
* [`opencoinage.Currency`][Currency]
* [`opencoinage.Token`][Token]
* [`opencoinage.Vocabulary`][Vocabulary]
* `opencoinage.util`
  * [`opencoinage.util.Base62`][util.Base62]
* `opencoinage.xmlrpc`
  * [`opencoinage.xmlrpc.Client`][xmlrpc.Client]

Examples
--------

    #!python
    import opencoinage

### Obtaining the OpenCoinage SDK version

    #!python
    opencoinage.__version__                 #=> "0.0.1"

### Encoding an integer into a Base62 string

    #!python
    TODO

### Decoding a Base62 string into an integer

    #!python
    TODO

Dependencies
------------

* [Python][] (>= 2.6)

Installation
------------

    #!bash
    sudo pip install opencoinage

Uninstallation
--------------

    #!bash
    sudo pip uninstall opencoinage

Mailing List
------------

<http://groups.google.com/group/opencoinage>

Source Code
-----------

<http://github.com/opencoinage/opencoinage>

License
-------

The OpenCoinage SDK is free and unencumbered [public domain][Unlicense]
software.

[Unlicense]:     http://unlicense.org/
[Python]:        http://python.org/
[Issuer]:        http://github.com/opencoinage/opencoinage/blob/master/src/python/opencoinage/issuer.py
[Currency]:      http://github.com/opencoinage/opencoinage/blob/master/src/python/opencoinage/currency.py
[Token]:         http://github.com/opencoinage/opencoinage/blob/master/src/python/opencoinage/token.py
[Vocabulary]:    http://github.com/opencoinage/opencoinage/blob/master/src/python/opencoinage/vocabulary.py
[util.Base62]:   http://github.com/opencoinage/opencoinage/blob/master/src/python/opencoinage/util/base62.py
[xmlrpc.Client]: http://github.com/opencoinage/opencoinage/blob/master/src/python/opencoinage/xmlrpc/client.py
