# milter-authlimit
Sendmail Milter filter to limit sending rate of SMTP AUTH mails

Sendmail Milter filter to limit sending rate of mails sent by authenticated users (SMTP AUTH). This is a small piece of software written in C from scratch. It uses few external modules : libmilter, GLib and libpthreads so it's easy to understand or audit the code.

This Milter does only two things :
1/ Limit mail sending rate for SMTP authenticated users (aka senders). If sender is unauthenticated this Milter does nothing. The limit is expressed in number of mails per time limit (minute, hour, day).
2/ A whitelist of IP addresses can be defined. For mails comming from one of these IP (typically internal networks) sending rate is unlimited.

