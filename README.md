# GMail-Subject-Header-Turkish-Char-Problem

If you have sent e-mails in a different language than English or using characters outside the ASCII range you have probably already used utf8 to send them.

Specifying the use of UTF-8 in the body of an e-mail is very similar to doing it for a HTTP response. You can specify the content-type in an e-mail header like this:

1
Content-Type: text/plain; charset=utf-8
But there is catch. The subject line of an e-mail is a header by itself, and headers must contain only ASCII characters. Happily, there is a work around. RFC 1342 is a recommendation that provides a way to represent non ASCII characters inside e-mail headers in a way that won’t confuse e-mail servers.

To encode a header using this technique you must use this format:

1
=?charset?encoding?encoded-text?=
And this is an example of its use:

1
=?utf-8?Q?hello?=
The encoding must be either B or Q, these mean base 64 and quoted-printable respectively. You can read the RFC 1342 document for more information about how they work.

I am going to show a snippet of how to use php’s mail function to send an e-mail using UTF-8 in the subject and content.

COPY: https://ncona.com/2011/06/using-utf-8-characters-on-an-e-mail-subject/
