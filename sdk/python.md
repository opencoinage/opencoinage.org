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
    from opencoinage.util import Base62
    
    Base62.encode(1234567890)               #=> "1LY7VK"

### Decoding a Base62 string into an integer

    #!python
    from opencoinage.util import Base62
    
    Base62.decode("1LY7VK")                 #=> 1234567890

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

Download
--------

* [opencoinage-0.0.0.tar.bz2][tar.bz2]
* [opencoinage-0.0.0.tar.gz][tar.gz]
* [opencoinage-0.0.0.zip][zip]

[PyPI]:    http://pypi.python.org/pypi/opencoinage
[tar.bz2]: http://pypi.python.org/packages/source/o/opencoinage/opencoinage-0.0.0.tar.bz2
[tar.gz]:  http://pypi.python.org/packages/source/o/opencoinage/opencoinage-0.0.0.tar.gz
[zip]:     http://pypi.python.org/packages/source/o/opencoinage/opencoinage-0.0.0.zip

Mailing List
------------

<http://groups.google.com/group/opencoinage>

Source Code
-----------

<http://github.com/opencoinage/opencoinage>

Authors
-------

* [Arto Bendiken](http://github.com/bendiken) - <http://ar.to/>

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
