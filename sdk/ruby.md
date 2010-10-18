Ruby Software Development Kit (SDK)
===================================

TODO

Classes
-------

* [`OpenCoinage::Issuer`][Issuer]
* [`OpenCoinage::Currency`][Currency]
* [`OpenCoinage::Token`][Token]
* [`OpenCoinage::Vocabulary`][Vocabulary]
* `OpenCoinage::Util`
  * `OpenCoinage::Util::Base62`
  * `OpenCoinage::Util::PKCS1`
* [`OpenCoinage::XMLRPC`][XMLRPC]
  * [`OpenCoinage::XMLRPC::Client`][XMLRPC::Client]
  * [`OpenCoinage::XMLRPC::Server`][XMLRPC::Server]

Examples
--------

    #!ruby
    require 'opencoinage'

### Obtaining the OpenCoinage SDK version

    #!ruby
    OpenCoinage::VERSION.to_s               #=> "0.0.1"

### Encoding an integer into a Base62 string

    #!ruby
    OpenCoinage::Base62.encode(1234567890)  #=> "1LY7VK"

### Decoding a Base62 string into an integer

    #!ruby
    OpenCoinage::Base62.decode("1LY7VK")    #=> 1234567890

Dependencies
------------

* [Ruby][] (>= 1.8.7) or (>= 1.8.1 with [Backports][])
* [Bitcache](http://rubygems.org/gems/bitcache) (>= 0.0.1)
* [RDF.rb](http://rubygems.org/gems/rdf) (>= 0.2.3)
* [RSA.rb](http://rubygems.org/gems/rsa) (>= 0.1.4)
* [UUID](https://rubygems.org/gems/uuid) (>= 2.3.1)

Installation
------------

    #!bash
    [sudo] gem install opencoinage            # Ruby 1.8.7+
    [sudo] gem install backports opencoinage  # Ruby 1.8.x

Uninstallation
--------------

    #!bash
    [sudo] gem uninstall opencoinage

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

[Unlicense]:      http://unlicense.org/
[Ruby]:           http://ruby-lang.org/
[Backports]:      http://rubygems.org/gems/backports
[Issuer]:         http://opencoinage.rubyforge.org/OpenCoinage/Issuer.html
[Currency]:       http://opencoinage.rubyforge.org/OpenCoinage/Currency.html
[Token]:          http://opencoinage.rubyforge.org/OpenCoinage/Token.html
[Vocabulary]:     http://opencoinage.rubyforge.org/OpenCoinage/Vocabulary.html
[XMLRPC]:         http://opencoinage.rubyforge.org/OpenCoinage/XMLRPC.html
[XMLRPC::Client]: http://opencoinage.rubyforge.org/OpenCoinage/XMLRPC/Client.html
[XMLRPC::Server]: http://opencoinage.rubyforge.org/OpenCoinage/XMLRPC/Server.html
