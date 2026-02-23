# kdesu-rust-workaround

This script and Config file temporarily fix kdesu when using sudo-rs

Affected Distros (That I know of):

Kubuntu (Affected since 25.10): ✅ (Fixed in kubuntu-settings-desktop(>=25.04.2.1) and ksystemlog(>=25.08.1-0ubuntu1.1), ❌ Discover link still broken ❌)

--------------------------------------------------------------------------
Installation:
- copy kdesu-sudo-wrapper into your home directory
- copy kdesurc config file into ~/.config
- Edit kdesurc (set command=... to the path where the wrapper is located)

        Example: "command=/home/user/kdesu-sudo-wrapper"
- Make kdesu-sudo-wrapper executable (right click -> Properties -> Permissions -> Check "Allow file to be executed as a program")

This script IS NOT intended to be a PERMANENT FIX to this issue and cannot accept more than 9 Arguments (command + 8)

DISCLAIMER: 

I am currently unsure about what security implications applying this workaround might have as the wrapper is located in the home directory

--------------------------------------------------------------------------
Where does this Issue come from? (This is only speculation though!)

kdesu seems to only accept output from sudo that has exactly one ":" symbol in it.

If there is more than one or none, the process will get stuck and the user is never prompted for authentication.

This has been fine for years, however, since Ubuntu is now Migrating to sudo-rs, this issue is arising for its users, as sudo-rs's prompt looks like this:

"[sudo: authenticate] Password:" -> More than one ":" Symbol => kdesu gets stuck => User never gets prompted.

Instead of this:

"[sudo] password for user user:" -> One ":" Symbol => kdesu recognizes prompt => User gets prompted for authentication.
