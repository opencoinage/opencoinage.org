Java Software Development Kit (SDK)
===================================

TODO

Classes
-------

* [`org.opencoinage.Issuer`][Issuer]
* [`org.opencoinage.Currency`][Currency]
* [`org.opencoinage.Token`][Token]
* [`org.opencoinage.Vocabulary`][Vocabulary]
* `org.opencoinage.util`
  * [`org.opencoinage.util.Base62`][util.Base62]
* `org.opencoinage.xmlrpc`
 * [`org.opencoinage.xmlrpc.Client`][xmlrpc.Client]

Examples
--------

    #!java
    import java.math.BigInteger;
    import org.opencoinage.*;

### Encoding an integer into a Base62 string

    #!java
    import org.opencoinage.util.Base62;
    
    Base62.encode(BigInteger.valueOf(1234567890)); // "1LY7VK"

### Decoding a Base62 string into an integer

    #!java
    import org.opencoinage.util.Base62;
    
    Base62.decode("1LY7VK");                       // 1234567890

Dependencies
------------

* [Java][] SE 6

Installation
------------

TODO

Uninstallation
--------------

TODO

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
[Java]:          http://www.java.com/
[Issuer]:        http://github.com/opencoinage/opencoinage/blob/master/src/java/org/opencoinage/Issuer.java
[Currency]:      http://github.com/opencoinage/opencoinage/blob/master/src/java/org/opencoinage/Currency.java
[Token]:         http://github.com/opencoinage/opencoinage/blob/master/src/java/org/opencoinage/Token.java
[Vocabulary]:    http://github.com/opencoinage/opencoinage/blob/master/src/java/org/opencoinage/Vocabulary.java
[util.Base62]:   http://github.com/opencoinage/opencoinage/blob/master/src/java/org/opencoinage/util/Base62.java
[xmlrpc.Client]: http://github.com/opencoinage/opencoinage/blob/master/src/java/org/opencoinage/xmlrpc/Client.java
