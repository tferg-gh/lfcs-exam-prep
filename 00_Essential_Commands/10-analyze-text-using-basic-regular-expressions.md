**regex**: Regular expressions. Used for complex searching. #regex 

**^ Carat**: The line begins with. The symbol appears at the beginning of the search pattern. #grep
```sh
grep '^PASS' /etc/login.defs
PASS_MAX_DAYS	99999
PASS_MIN_DAYS	0
PASS_WARN_AGE	7
```

**$ Dollar Sign**: The line ends with. The symbol appears at the end of the search pattern. #grep
``` sh
grep '7$' /etc/login.defs
ERASECHAR	0177
PASS_WARN_AGE	7
```

**. Period**: Match any ONE character. The symbol appears where the character would be. #grep
``` sh
grep -r 'c.t' /etc
..
/etc/update-motd.d/88-esm-announce:[ ! -r "$stamp" ] || cat "$stamp"
/etc/update-motd.d/91-contract-ua-esm-status:[ ! -r "$stamp" ] || cat "$stamp"
/etc/update-motd.d/90-updates-available:[ ! -r "$stamp" ] || cat "$stamp"
/etc/update-motd.d/85-fwupd:        cat /run/motd.d/85-fwupd
```
Escape characters using a **backslash** before it to stop any special function and treat it like the symbol. #escape-character #regex #grep #egrep 

**\* Asterix**: Match the previous element 0 or more times. Symbol appears before final **optional** character in search pattern. #grep
``` sh
grep -r '/.*/' /etc/
..
/etc/update-motd.d/85-fwupd:#!/bin/sh
/etc/update-motd.d/85-fwupd:if [ -f /run/motd.d/85-fwupd ]; then
/etc/update-motd.d/85-fwupd:        cat /run/motd.d/85-fwupd
```

**+ Plus**: Match the previous element 1 or more times. Symbol appears before final **required** character in search pattern. #egrep
``` sh
grep -r '0\+' /etc/
/etc/update-motd.d/00-header:#    00-header - create the header of the MOTD
/etc/update-motd.d/00-header:#    Copyright (C) 2009-2010 Canonical Ltd.
/etc/update-motd.d/00-header:#    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.
```

**Note**: In basic regular expressions the meta-characters **?, +, {, |, (, and )** lose their special meaning; instead use backslashed versions. #grep #egrep #escape-character #regex 

[[11-extended-regular-expressions]]