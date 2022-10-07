###### PAM = Pluggable Authentication Module
Allows us to plug in various modules that help us determine how different utilities handle authentication

This is a very powerful API that provides very granular control over authentication, the conditions to grant authentication and the behviours on failure. 

Files are located here in this folder:

###### File locations #etc-pamd
```
/etc/pam.d/
``` 
This contains all the authentication instructions for each utility as listed:

```sh 
tom@ubuntu:~$ sudo ls /etc/pam.d
atd		         common-session			        gdm-password  runuser
chfn		     common-session-noninteractive	login	      runuser-l
chpasswd	     cron				            newusers      sshd
chsh		     cups				            other	      su
common-account	 gdm-autologin			        passwd	      sudo
common-auth	     gdm-fingerprint		        polkit-1      su-l
common-password  gdm-launch-environment		    ppp	          systemd-user

```
Each of these is a file that contains instructions for how PAM is to handle authentication for each of these modules

``` sh
tom@ubuntu:~$ sudo cat /etc/pam.d/su
#
# The PAM configuration file for the Shadow `su' service
#

# This allows root to su without passwords (normal operation)
auth       sufficient pam_rootok.so

# Uncomment this to force users to be a member of group root
# before they can use `su'. You can also add "group=foo"
# to the end of this line if you want to use a group other
# than the default "root" (but this may have side effect of
# denying "root" user, unless she's a member of "foo" or explicitly
# permitted earlier by e.g. "sufficient pam_rootok.so").
# (Replaces the `SU_WHEEL_ONLY' option from login.defs)
# auth       required   pam_wheel.so

# Uncomment this if you want wheel members to be able to
# su without a password.
# auth       sufficient pam_wheel.so trust

# Uncomment this if you want members of a specific group to not
# be allowed to use su at all.
# auth       required   pam_wheel.so deny group=nosu

# Uncomment and edit /etc/security/time.conf if you need to set
# time restrainst on su usage.
# (Replaces the `PORTTIME_CHECKS_ENAB' option from login.defs
# as well as /etc/porttime)
# account    requisite  pam_time.so

# This module parses environment configuration file(s)
# and also allows you to use an extended config
# file /etc/security/pam_env.conf.
# 
# parsing /etc/environment needs "readenv=1"
session       required   pam_env.so readenv=1
# locale variables are also kept into /etc/default/locale in etch
# reading this file *in addition to /etc/environment* does not hurt
session       required   pam_env.so readenv=1 envfile=/etc/default/locale

# Defines the MAIL environment variable
# However, userdel also needs MAIL_DIR and MAIL_FILE variables
# in /etc/login.defs to make sure that removing a user 
# also removes the user's mail spool file.
# See comments in /etc/login.defs
#
# "nopen" stands to avoid reporting new mail when su'ing to another user
session    optional   pam_mail.so nopen

# Sets up user limits according to /etc/security/limits.conf
# (Replaces the use of /etc/limits in old login)
session    required   pam_limits.so

# The standard Unix authentication modules, used with
# NIS (man nsswitch) as well as normal /etc/passwd and
# /etc/shadow entries.
@include common-auth
@include common-account
@include common-session

```

The instructions are formed thusly:

type | control | module path | module arguments

For detailed instructions of each component of the instruction see:

###### man page
```sh
man pam.conf
```

Essentially the API runs through each instruction testing it, in order of top to bottom and performs actions based on that configuration to provide a user access. 

###### Module Type
**Account:** Takes some actions related to the user account. Like restricting access after 5pm.
**Auth:** Used to establish the identity of a user or program or grant additional privelages after successful authentication
**Password:** Usually used to update a password or a secret key.
**Session**: Used to prepare the user session in some way.

###### Control Field
Typically the instructions are tested from top to bottom but the control fields can change this behaviour. 
**Required**: Needs all of these conditions to succeed otherwise the authentication fails. This AND that. Will move on to other modules on failure. 
**Sufficient**: Needs at least on of these conditions to be successful. This OR that. Will usually be enough to complete authentication. 
**Requisite**: A stronger version of **Required**. If this fails, don't progress any further. 
**Optional**:
**Include**:
**Substack**: 

**Module Path** **& Arguments**
These are various functions we can use with PAM. Check the man pages of each module to find more information on how each one is used:
```sh
tom@ubuntu:~$ man pam # tab here with no space after pam
pam                  pam_ftp              pam_securetty
pam_access           pam_getenv           pam_selinux
pam-auth-update      pam_group            pam_sepermit
pam_cap              pam_issue            pam_shells
pam.conf             pam_keyinit          pamstack
pamcut               pam_lastlog          pamstretch
pam.d                pam_limits           pamstretch-gen
pam_debug            pam_listfile         pam_succeed_if
pamdeinterlace       pam_localuser        pam_systemd
pam_deny             pam_loginuid         pam_tally
pamdice              pam_mail             pam_tally2
pam_echo             pam_mkhomedir        pam_time
pam_env              pam_motd             pam_timestamp
pam_env.conf         pam_namespace        pam_timestamp_check
pam_exec             pam_nologin          pam_tty_audit
pam_extrausers       pamoil               pam_umask
pam_faildelay        pamon                pam_unix
pam_faillock         pam_permit           pam_userdb
pamfile              pam_pwhistory        pam_warn
pam_filter           pam_rhosts           pam_wheel
pam_fprintd          pam_rootok           pam_xauth
```

Essentially, these instructions are saying:

Here is the type of module this is, here is what I want you to do on a success or failure, and here is the module and it's arguments we're presenting. 

