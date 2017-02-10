# noEnumerato

=== Stop User Enumeration ===
Original Author: Locally Digital Ltd
Contributors: fullworks, ihateonions
Tags: User Enumeration, Security, WPSCAN, fail2ban
Requires at least: 3.4
Tested up to: 4.3.1
Stable tag: 1.3.3
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

User Enumeration is a method hackers and scanners use to get your username. This plugin stops it.
== Description ==
Even if you are careful and set your blogging nickname differently from your login id, if you are using permalinks it only takes a few seconds
to discover your real user name. This plugin stops user enumeration dead (like in use by WPSCAN), and additionally it will log an event
in your system log so you can use (optionally) fail2ban to block the probing IP.
== Installation ==

1. Upload `plugin-name.php` to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress

== Frequently asked questions ==

= Are there any settings? =
No
= Will it work on Multisite? =
Yes
= Do I need fail2ban for this to work? =
No, but fail2ban will allow you to block IP addresses that attempt user enumeration.
= What do I do with the fail2ban file?=
Place  the file wordpress-userenum.conf in your fail2ban installation's filter.d directory.
edit your jail.local  to include lines like
`[wordpress-userenum]
enabled = true
filter = wordpress-userenumaction   = iptables-allports[name=WORDPRESS-USERENUM]
           sendmail-whois-lines[name=WORDPRESS-USERENUM, dest=youremail@yourdomain, logpath=/var/log/messages]
logpath = /var/log/messages
maxretry = 1
findtime = 600
bantime = 2500000`
Adjusted to your own requirements.

== Change Log ==

= 1.0 =
*  first release

== Upgrade notice ==
