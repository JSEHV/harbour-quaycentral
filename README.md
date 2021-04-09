# CentralQuay
A GUI app for the 1Password command-line tool on Sailfish OS.

CentralQuay is an unofficial application and is in no way associated with 1Password or AgileBits, Inc.

Licensed under GNU GPLv3.

<h3>Rationale</h3>

- Having a 1Password client that keeps Ambience on user's device, providing for a better and more consistent SFOS experience.
- Official 1Password app that supports 1Password.com accounts requires Android version 5 or greater and is therefore incompatible with Alien Dalvik on Xperia X.
- Overall plus to have more native SFOS apps and fewer dependencies on Android versions.

<h3>Requirements</h3>

- Installation of the 1Password command-line tool in /usr/local/bin or another directory in your $PATH. (The app has not been tested with the tool in a location other than /usr/local/bin).

- Adding the shorthand <centquaysfos> as a method of signing in to the CLI. Further rationale for this under Privacy & Security. The shorthand is device-specific. Even if user has already signed in for the first time, a new shorthand may be added by signing in again with domain, email and secret key. More info on adding the shorthand is available at:<br>
    https://support.1password.com/command-line-reference/#options-for-signin &<br>
    https://1password.community/discussion/comment/561753/#Comment_561753

<h3>Limitations & Issues</h3>

- As of now, only shows items in 'Login' category and there just has usernames, passwords, and one-time passwords (if applicable). Plan to add more categories and eventually all.
- Read-only, planning to add editing capability at some point.
- Timeout only applies to the app's interaction with the CLI, i.e. swiping back a page, going to Settings, or scrolling down a list, etc. will not reset the lockout timer.
- Leaving the app open on an item details page that includes a TOTP (one-time password) will mean the lockout timer never times out, as it will keep resetting every 30 seconds a new code is generated.
- No support for multiple accounts or for groups. App is intended for individual use.
- Option to select a default vault and possibly more vault management, similar to the official app, is on hold until I have a Sailfish Secrets implementation to provide the secure storage that may be required for data such as a default vault UUID.
- Clipboard icon on item details page may be somewhat misaligned if the system font size is enlarged in Settings. Will edit code to work around this somehow, prefer the medium clipboard icon to the small one, there is no small-plus icon size for the clipboard icon.
- Lock icon on cover may appear somewhat smaller than other standard cover icons. No lock icon available under the Cover category so went with the small icon for now.
- Need to look at consolidating some of the processes to reduce the overall number, not an urgent issue but a change that may improve performance by reducing resources used by the app, and it is possible that there don't need to be as many.
- No setup screen to allow user to enter necessary credentials to signin with the app for the first time and avoid having to add the shorthand manually in Terminal. May add this later, clearing all fields as soon as data is passed to the CLI as is done with the master password. With the pre-determined centquaysfos shorthand, there's currently no need for the storage of any secrets, i.e. user's own domain/shorthand.
- Button on Settings page meant to signout and forget the CentralQuay shorthand does not function and may require that the user first removes the CLI on that device from their list of authorized devices on their profile page at my.1password.com, followed by a device restart and then would have to get back into Terminal to complete with the 'forget' command. This removes the justification for the button being in Settings in the app, since user would have to re-verify the app to get to it. Will re-check functionality in future CLI versions as this would be a cleaner and more preferrable way to allow the user to remove login access to their Vaults from CentralQuay for any given reason, easily and quickly. This issue has been discussed on the 1Password Community support pages and can be read about here:<br>
    https://1password.community/discussion/119973/can-not-signout-account
- No icon yet.

<h3>User Privacy & Security</h3>

By assigning the shorthand <centquaysfos>, app is able to avoid requiring any secrets to be stored. User also has control over what accounts that shorthand is associated with, incase they'd like to use the CLI for separate accounts and not use a GUI for all, or to continue using the CLI after revoking CentralQuay login access, etc. While the default domain value <my> is now the only option available to new users, it was the case previously that personalized domains could be chosen, hence the classification of this information as secret.

Master password entered by user is cleared immediately following its passing to the CLI and is never stored.

User is responsible once a password is copied to the clipboard. Intend to add optional timer (similar to official apps) so that user can designate a time after which clipboard is cleared following a password or username being copied. It will require a variable string in RAM to cross reference clipboard contents (and avoid deleting unrelated data that user may have put on clipboad in the meantime), after which both clipboard and variable string will be cleared.

<h3>Miscellaneous</h3>

If you would like to send feedback regarding the app, please email mjbarrett@eml.cc

Source code is available at: https://github.com/michaeljohnbarrett/harbour-centralquay

If you would like to support my work in developing native Sailfish OS apps (this would inch my status closer to full-time developer), you may do that here -- https://www.buymeacoffee.com/michaeljb <br>
<br>
	Thanks,<br>
		Michael Barrett
