Frequently Asked Questions (FAQ)
================================

## Why are tokens encoded using Base62 instead of Base64? {#base62}

Base62 is similar to [Base64][] but drops the two non-alphanumeric
characters, `+` and `/`, which are problematic in many contexts such as in
filenames and URLs. Dropping these characters also improves usability on
many operating systems by autoselecting the entire token string when
double-clicked, thus facilitating copy and paste.

[Base64]: http://en.wikipedia.org/wiki/Base64
