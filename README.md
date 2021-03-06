d-note
======

Fork information
================
This is a fork of atoponce/d-note because it was not being maintained.
I have made several changes to securely run this as a company service:

 - IPTables bruteforce protection
 - Generate URL (Note ID) on server, not by the client
 - Improved Apache configuration
   - Adjusted Logging using LogFormat to not log the actual request; otherwise it would leak URL (Note ID) information in logs.
     These could actually be used if for example a Note was requested with a wrong password.
   - End security related headers
   - Rewrite IP based requests to actual hostname to match TLS certificate
   - Make it possible to separate access between being able to POST a Note and to READ a note
   - Rewrite certain requests so the program uses the 404 error template instead of Apache giving an error
   - Improve SSL configuration
 - Added ASCII input validation on hashcash input
 - Added crontab information to delete old notes (30 days)
 - Added input validation on URL to avoid Apache 500 errors caused by padding problem with invalid, too long or short URLs
 - Added rel="noreferrer" to all links to avoid browser referrer header leakage

See the Wiki for more information. I have put up some information which should help you get your copy up and running.

27-02-2017 I have seen activity in the original project, that's good news! I want to contribute with certain commits soon.
           I do probably have some plans on my own so i'll keep this fork alive for now.

 With kind regards,
     Thijssss

Background
----------

d-note is a self destructing notes web application that you can run on your own
server. A message is created using the web form, and when submitted, a link is
returned that you then send to the recipient. When the recipient opens the
link, the message is displayed and immediately destroyed on the server. Thus,
the link can never be used again for displaying the same note.

See [the installation instructions](/INSTALL.md) on how to install this on your
server.

Read [the documentation](/doc) about further information regarding this
project.

This project is licensed under the GNU Affero General Public License, version 3,
unless otherwise stated. See [the license](LICENSE.md) for the complete license.

Demo
----

If you would like to test drive d-note, I have it running at https://ae7.st/d/.
Currently, it is hosted using a self-signed certificate. As such, the
fingerprints of the certificate are:

    MD5: 5A:E1:4E:B6:31:B8:3D:69:B1:D6:C0:A7:6B:46:FE:67
    SHA1: 55:89:CD:C0:D4:85:CC:A5:DE:30:11:5D:9C:C9:12:1C:5C:9D:10:C5
    SHA256: 12:91:BB:4C:E8:2F:1C:0C:D9:96:AF:4E:1D:8C:F7:B0:A8:07:70:C5:9C:89:B8:94:EE:E2:2A:D6:19:43:17:A4
