Frequently Asked Questions (FAQ)
================================

## Technical Questions

### Why are tokens encoded using Base62 instead of Base64? {#token-base62}

Base62 is similar to [Base64][] but drops the two non-alphanumeric
characters, `+` and `/`, which are problematic in many contexts such as in
filenames and URLs. Dropping these characters also improves token usability
in many environments by enabling the autoselection of entire token strings
when double-clicked, thus facilitating copy and paste operations.

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

In general, wallet software should be designed to abstract away and hide
low-level details like token strings from users, not to promote their
(misleading) purported readability.

Further, in contexts where raw token identifiers do happen to get passed
around directly (e.g. in SMS messages and Twitter direct messages),
metadata would just add noise and bloat - quite possibly causing
peer-to-peer token transfer messages to exceed transport limitations (160
and 140 characters, respectively, in the aforementioned two mediums).

[Yodelbank]: http://web.archive.org/web/20050901141955/http://yodelbank.com/certificates.html
[eCache]:    https://ffij33ewbnoeqnup.onion.meshmx.com/readme.php
