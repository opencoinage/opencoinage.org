Frequently Asked Questions (FAQ)
================================

Here follow some frequently-asked questions, with answers. If you have a
question not covered here, please write to the [mailing list][].

[mailing list]: http://groups.google.com/group/opencoinage

[TOC]

## Technical Questions {#technical}

### Which cryptographic schemes does OpenCoinage support? {#crypto-schemes}

OpenCoinage is designed to accommodate a variety of cryptographic schemes
for digital cash. In the abstract, OpenCoinage tokens are simply two-tuples
consisting of a token identifier and the issuer's cryptographic signature of
the identifier. Both the token identifier and the signature are
arbitrary-length integers and can thus accommodate any cryptographic
algorithm, key length, and hash function. The OpenCoinage protocols are
designed to support cryptographic schemes all the way from simple
[HMACs][HMAC] to full [blinded][blind signature] Chaumian digital cash.

[HMAC]:            http://en.wikipedia.org/wiki/HMAC
[blind signature]: http://en.wikipedia.org/wiki/Blind_signature

### Why are tokens encoded using Base62 instead of Base64? {#token-base62}

Base62 is similar to [Base64][] but drops the two non-alphanumeric
characters, `+` and `/`, which are problematic in many contexts such as in
filenames and URLs. Dropping these characters also improves token usability
in many environments by enabling the autoselection of entire token strings
when double-clicked, thus facilitating copy-and-paste operations.

[Base64]: http://en.wikipedia.org/wiki/Base64

### Why don't tokens include a human-readable metadata part? {#token-metadata}

[Some][Yodelbank] [previous][eCache] digital cash systems have been designed
around purported human-readable token formats; in such schemes, the
cryptographic portion of the token is typically preceded by a human-readable
metadata prefix that spells out the currency identifier, value amount, and
expiration date of the token.

The problem with such schemes is that any associated human-readable metadata
would necessarily have to be considered entirely untrustworthy in terms of
describing the actual worth of the token. Altering the value amount of a
token would invalidate the cryptographic signature on the token, yes, but
that is not something that a human user is equipped to detect just by
looking at the token. The only way to validate that a token actually is
what the human-readable metadata claims it to be would be to pass the token
to some piece of software capable of determining what's what.

Given that, it would be a terrible idea to promote human-readable token
metadata as providing any useful or trustworthy information about the
contents of a token. Since properly validating a token can only be done
with software, not having a metadata prefix mandates such a procedure for
checking token worth and validity, helping ensure that at least one
particular class of attempted fraud will not be encouraged with OpenCoinage
tokens.

In general, wallet software should be designed to abstract and hide away
low-level details like token strings from users, not to promote their
(misleading) purported readability.

Further, in contexts where raw token identifiers do happen to get passed
around directly (e.g. in SMS messages and Twitter direct messages),
metadata would just add noise and bloat - quite possibly causing
peer-to-peer token transfer messages to exceed transport limitations (160
and 140 characters, respectively, in the aforementioned two mediums).

[Yodelbank]: http://web.archive.org/web/20050901141955/http://yodelbank.com/certificates.html
[eCache]:    https://ffij33ewbnoeqnup.onion.meshmx.com/readme.php

## Developer Questions {#developer}

### How do I submit bug reports and patches for OpenCoinage? {#bug-reports}

Submit any bug reports to our [issue tracker][] on [GitHub][]. If you have a
patch that fixes a bug you ran into, you can either attach it to the issue,
or you can fork the code base on GitHub ([see below](#contributing)) and
send us a pull request. We prefer pull requests, but patch files are fine,
too.

If you have any questions related to a bug or other problem you're
experiencing, just post to the [mailing list][] and we'll be happy to try
and help you out.

[issue tracker]: http://github.com/opencoinage/opencoinage/issues

### How can I get involved in developing OpenCoinage? {#contributing}

First off, be sure to join the [mailing list][] to keep abreast of ongoing
developments.

Once you know what you want to work on, [fork][] the OpenCoinage code on
[GitHub][]. Implement your contribution on a [topic branch][] (**not** on
the _master_ branch), and when done, send us a [pull request][] to request
that we review and merge your contribution.

Note the following dos and don'ts for working on the code base:

* Do your best to adhere to the existing coding conventions and idioms, so
  that the developer reviewing and merging your code won't need to do
  extra work to clean up your code, which could delay processing your
  contribution.
* Don't use hard tabs, and don't leave trailing whitespace on any line.
* Do document every method you add using the appropriate inline annotations
  for the particular programming language used ([YARD][] for Ruby,
  [Javadoc][] for Java, etc).  Look at the existing code for examples.
* Don't touch any `VERSION` or `AUTHORS` files. If you need to change them,
  do so on a private branch only.
* Do feel free to add yourself to the `CREDITS` file and the corresponding
  list in the `README`. Alphabetical order (last name, first name) applies.

Note also that in order for us to merge any non-trivial changes (as a rule
of thumb, additions larger than about 15 lines of code) we will need an
explicit [public domain dedication][PDD] on record from you. We need this in
order to ensure that OpenCoinage remains completely free and unencumbered by
any copyright claims or concerns. Prepare your public domain dedication [as
instructed][PDD], and e-mail it to the mailing list with the subject
_"Public domain dedication"_ so that it becomes a matter of public record.

If you wish to contribute to OpenCoinage pseudonymously, that's perfectly
fine with us; but we will still require a valid e-mail address to record
your contributions with, and a public domain dedication on record as having
been sent from that e-mail address.

[GitHub]:       http://github.com/opencoinage
[fork]:         http://help.github.com/forking/
[topic branch]: http://github.com/dchelimsky/rspec/wiki/topic-branches
[pull request]: http://help.github.com/pull-requests/
[YARD]:         http://yardoc.org/
[Javadoc]:      http://www.oracle.com/technetwork/java/javase/documentation/index-137868.html
[PDD]:          http://unlicense.org/#unlicensing-contributions
