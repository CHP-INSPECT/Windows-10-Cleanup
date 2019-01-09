# Windows-10-Cleanup
A guide for Decluttering Windows 10 Builds.

### Content Classification
This repository is public-facing. All content posted to this guide should fall within Public or Non-Business designations.

### Intended Audience
This guide is intended for PC users who have been upgraded to Windows 10 in the 2018/19 conversion. Its purpose is to bring together information and recommendations that end users can implement to enhance their experience with their new machine.

### Authorship
This guide was produced by Aaron Fisher, but is open for updates.

# Contents
- [Removing Configuration Scripts](#removing-configuration-scripts)
- [Microsoft Store Cleanup](#microsoft-store-cleanup)
- [Add/Remove Programs](#addremove-programs)
- [Removing XBox and XBox Live Compatibility](#removing-xbox-and-xbox-live-compatibility)
- [Recommended Browsers](#recommended-browsers)
- [Deescalating LSIAgent Privileges for Chrome](#deescalating-lsiagent-privileges-for-chrome)

## Removing Configuration Scripts
Depending on how your migration was performed, there may be several IT scripts and tools left around on the Desktop.

Essential Windows files will never be stored on your desktop, so any objects there that you don't need or understand can safely be removed.

This typically includes .bat or .lnk files, as well as shortcuts to IT files on corporate servers.

## Microsoft Store Cleanup
The Microsoft Store App is installed by default on Windows machines. As one of the core windows apps, it can't be easily removed. However
it is the source of some preinstalled or prepurchased apps which can easily be removed.

Open this app by pressing the Windows key, and typing in "Microsoft Store". Once there, clicking the More Options icon ("..."), then clicking My Library will open up a list of all programs purchased or installed through the Microsoft Store.

From here, several undesired programs can be uninstalled.

Two applications, "Twitter" and "Candy Crush Saga" cannot be removed from the list, presumably due to Microsoft's agreement with the related companies. They will always show as "Purchased minutes ago", but are really just a built-in feature of the store. However they can be hidden from view by clicking the More Options icon, then clicking "Hide".

## Add\/Remove Programs
Open the Add/Remove Programs application by pressing the Windows key and typing "add". From here, you will see a long list of programs installed on your PC.

Nothing here is required by the operating system, however some may be required for correct operation of company services. In general, it is fairly safe to remove programs from this list, as they can easily be reinstalled if required. However, some user knowledge may be required to determine what should or shouldn't be removed.

Certain applications on this list, such as those associated with XBox or XBox Live may not be able to be removed this way. Additional steps required to remove these packages are detailed below.

## Removing XBox and XBox Live Compatibility
Depending on your department role, full integration between your PC and company-issued XBox entertainment consoles may not be required. Removing the utilities and adware support for XBox features may be done using the Windows Powershell.

To open Windows Powershell, press the Windows key and type "power". Right-click on the Windows PowerShell icon and select "Run as Administrator". You will be prompted for your username and password.

In Powershell, type the following command and press Enter:

> Get-AppxPackage \*Xbox\* | Remove-AppxPackage

Once run, this command should successfully remove all XBox packages except for Microsoft.XboxGameCallableUI. The attempt to remove Microsoft.XboxGameCallableUI will produce an error message, but that is fine. That particular package is protected for reasons outside the scope of this article.

Some additional packages may be uninstalled here, but this is only recommended for users with PowerShell experience.

## Recommended Browsers
Windows 10 is installed with Microsoft Edge and Internet Explorer 10 by default.

Due to the history of security flaws, compatibility issues, and poor user experience, it is recommended that Internet Explorer be completely removed from the system and replaced by a modern browser of your choice. This author recommends Google Chrome, due to its outstanding security features.

Leaving Internet Explorer installed is not recommended as some shortcuts and programs may launch Internet Explorer processes if it is installed, regardless of preferred browser settings. Windows updates may also periodically set the preferred browser back to IE if it remains installed.

## Deescalating LSIAgent Privileges for Chrome
If using the Chrome browser, it is recommended for security reasons to deescalate privileges given to LSIAgent.

LSIAgent is an app which monitors process behavior and system resource usage on endpoint devices. It contains a lot of useful information for network administrators, some of which may be useful for users as well.

The full list of data it is collecting can be found at "C:\Program Files (x86)\SysTrack\LsiAgent\MDB\collect.mdb".

However, the lsiwebhook extension, which it uses to pull additional process-specific information from Chrome has overly broad privileges. This loose control over accessibility and scope poses both security and privacy concerns. Until such a time as that is corrected, it is recommended to remove this app.

The best way to do so is by deleting the lsiwebhook extension.

Find the lsiwebhook extension ID by going to chrome://extensions/ and noting the listed ID. Then, go to "C:\Users\User_Name\AppData\Local\Google\Chrome\User Data\Default\Extensions" and delete the folder with the corresponding ID.
