# milter-authlimit
Sendmail Milter filter to limit sending rate of SMTP AUTH mails

milter-authlimit is a [Sendmail](http://www.sendmail.org "MTA: Mail Transport Agent") [Milter](https://en.wikipedia.org/wiki/Milter). It's a daemon running in the background called by Sendmail for each incoming mail. milter-authlimit doesn't modify mails it just accept them or reject them. It's goal is to limit sending rate of mails sent by authenticated users (SMTP AUTH). This is a small piece of software written in C from scratch. It uses few external modules : libmilter, GLib and libpthreads so it's easy to understand or audit the code.

This Milter does only two things :<br>
<ol>
<li>Limit mail sending rate for SMTP authenticated users (aka senders). If sender is unauthenticated this Milter does nothing. The limit is expressed in number of mails per time unit (minute, hour, day).
<li>A whitelist of IP addresses or IP subnets (CIDR) may be defined. For mails comming from one of these IP (typically internal networks) sending rate is unlimited.
</ul>
