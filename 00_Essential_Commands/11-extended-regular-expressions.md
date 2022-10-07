[[10-analyze-text-using-basic-regular-expressions]]

**+ Plus**: Match the previous element 1 or more times. Symbol appears before final **required** character in search pattern. #egrep-plus
``` sh
grep -Er '0+' /etc/ # -E for extended regular expressions
/etc/update-motd.d/00-header:#    00-header - create the header of the MOTD
/etc/update-motd.d/00-header:#    Copyright (C) 2009-2010 Canonical Ltd.
/etc/update-motd.d/00-header:#    51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA.

OR

egrep -r '0+' /etc/ # will do the same thing as -E in grep
```

**{ } Braces**: Previous element can exist "this many" times. **{min,max}** Place **after** previous element. #egrep-braces
``` sh
egrep -r '0{3,}' /etc/ # at least three instances of 0
..
/etc/login.defs:UID_MIN			 1000
/etc/login.defs:UID_MAX			60000
/etc/login.defs:GID_MIN			 1000
/etc/login.defs:GID_MAX			60000
..
egrep -r '0{3}' /etc/ # exaclty three instances of 0

egrep -r '0{,3}' /etc/ # at most three instances of 0
```
Note: Blank means no limit. 

**? Question mark**: Previous element is optional. Place **after** previous element. #egrep-question-mark
``` sh
egrep -r 'disabled?' /etc/
/etc/sysctl.conf:# settings are disabled so review and enable them as needed.
/etc/sysctl.conf:# 0=disable, 1=enable all, >1 bitmask of sysrq functions
```

**| Pipe**: Match one thing or the other. Place between two search terms. #egrep-pipe
```sh
egrep -ir 'enabled?|disabled?' /etc/
..
/etc/update-motd.d/50-motd-news:# Exit immediately, unless we're enabled
/etc/update-motd.d/50-motd-news:# This makes this script very easy to disable in /etc/default/motd-news configuration
/etc/update-motd.d/50-motd-news:[ "$ENABLED" = "1" ] || exit 0
```

**[ ] Square Brackets**: Match any one in a range or sets. Place where character can substituted. #egrep-square-brackets
``` sh
egrep -r 'c[au]t' /etc/ # returns cat or cut
..
/etc/update-motd.d/50-motd-news:	cat "$1" | head -n 10 | tr -d '\000-\011\013\014\016-\037' | cut -c -80
/etc/update-motd.d/50-motd-news:        cloud_id=$(cut -c -40 "${CLOUD}" | tr -c -d '[:alnum:]')
..
```

**( ) Parentheses**: Subexpressions or nested expressions. These search patterns are resolved first before continuing. #egrep-parentheses
```sh
egrep -ir '/dev/([a-z]*[0-9]?)*' /etc/ 
..
/etc/sane.d/microtek.conf:/dev/scanner
/etc/sane.d/kodak.conf:#scsi /dev/sg1
/etc/sane.d/fujitsu.conf:#scsi /dev/sg1
/etc/sane.d/fujitsu.conf:#usb /dev/usb/scanner0
/etc/sane.d/matsushita.conf:/dev/scanner
..
```

**\[^\] Carated Square Brackets**: Negates a range or set. Surround element with square brackets, with carat at the beginning.
#egrep-carated-square-brackets
``` sh
egrep -r 'http[^s]' /etc/ # will return all http but not https
..
/etc/ssl/openssl.cnf:#nsCaRevocationUrl		= http://www.domain.dom/ca-crl.pem
/etc/ssl/openssl.cnf:#nsCaRevocationUrl		= http://www.domain.dom/ca-crl.pem
..
```

[regexr.com](https://regexr.com)


