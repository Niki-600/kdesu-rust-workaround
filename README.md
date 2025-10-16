# kdesu-rust-fix

This script and Config file temporarily fix kdesu when using sudo-rs

--------------------------------------------------------------------------
Installation:
- copy kdesu-sudo-wrapper into your home directory
- copy kdesurc config file into ~/.config
- Edit kdesurc (set command=... to the path where the wrapper is)
      Example: "command=/home/user/kdesu-sudo-wrapper"

This script IS NOT intended to be a PERMANENT FIX to this issue and cannot accept more than 9 Arguments (sudo + 8)

DISCLAIMER: 

I am currently unsure about what security implications applying this fix might have

--------------------------------------------------------------------------
Where does this Issue come from?

kdesu seems to only accept output from sudo that has exactly one ":" symbol in it.

If there is more than one or none, the process will get stuck and the user is never prompted for authentication.

This has been fine for years, however, since Ubuntu is now Migrating to sudo-rs, this issue is arising for its users, as sudo-rs's prompt looks like this:

"[sudo: authenticate] Password:" -> More than one ":" Symbol => kdesu gets stuck => User never gets prompted.

Instead of this:

"[sudo] password for user user:" -> One ":" Symbol => kdesu recognizes prompt => User gets prompted for authentication.
