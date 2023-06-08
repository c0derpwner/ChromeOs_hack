# MY CASE


I've been contacted by one guy who said... "my pc it's really slow!" .. i would say it's classic for our subject.
So he gave me a `HP chromebook 14a na0019cl`.
Purpouse of the challenge was to boot a native lite distro of Linux.



## The problems 


With the support of coreboot and google i was able to map every boot mode allowed by that bootloader!


Normal/Verified Boot Mode

-    Can only boot Google-signed ChromeOS images
-    Full verification of firmware and OS kernel
-    No root access to the system, no ability to run Linux or boot other OSes
-    Automatically enters Recovery Mode if any step of Verified Boot fails
-    Default / out-of-the-box setting for all ChromeOS devices

Recovery Mode

-    User presented with Recovery Mode boot screen (white screen with 'ChromeOS is missing or damaged' text)
-    Boots only USB/SD with signed Google recovery image
-    Automatically entered when Verified Boot Mode fails
-    Can be manually invoked:
-    On Chromebooks, via keystroke: [ESC+Refresh+Power]
-    On Chromeboxes, by pressing a physical recovery button at power-on
-    On Convertibles/Tablets, by pressing/holding the Power, Vol+, and Vol- buttons for 10s and then releasing
-    Allows for transition from Verified Boot Mode to Developer Mode
-    On Chromebooks/Chromeboxes, via keystroke: [CTRL+D]
-    On Convertibles/Tablets, via button press: Vol+/Vol- simultaneously
-    Booting recovery media on USB/SD will completely repartition/reformat internal storage and reload ChromeOS (as well as some RW firmware components)

Note: The ChromeOS recovery process does not reset the firmware boot flags (GBB Flags), so if those are changed from the default, they will still need to be reset for factory default post-recovery.
Developer Mode

-    "Jailbreak" mode built-in to every ChromeOS device
-    Loosened security restrictions, allows root/shell access, ability to run Linux via crouton
-    Verified Boot (signature checking) disabled by default, but can be re-enabled
-    Enabled via [CTRL+D] on the Recovery Mode boot screen
-    Boots to the developer mode boot screen (white screen with 'OS verification is off' text), from which the user can select via keystroke where to boot:
-       ChromeOS (in developer mode) on internal storage ( [CTRL+D] )
-       ChromeOS/ChromiumOS on USB ( [CTRL+U] )
-       Legacy Boot Mode ( [CTRL+L] )
-    Boot screen displays the ChromeOS device/board name in the hardware ID string (eg, PANTHER F5U-C92, which is useful to know in the context of device recovery, firmware support, or in determining what steps are required to install a given alternate OS on the device.

Legacy Boot Mode

-    Unsupported (by Google) method for booting alternate OSes (Linux, Windows) via the SeaBIOS firmware payload / RW_LEGACY firmware region
-    Accessed via [CTRL+L] on the developer mode boot screen
-    Requires explicit enabling in Developer Mode via command line: sudo crossystem dev_boot_legacy=1 (installing RW_LEGACY firmware via the Firmware Utility Script will set this for you)
-    Not all ChromeOS devices are capable out of the box, most require a RW_LEGACY firmware update first
    Boots to the (black) SeaBIOS splash screen; if multiple boot devices are available, a prompt to show the boot menu will be displayed.


