With HACKER firmware Version 5.3 or higher, some things got changed and enhanced.

Changes and enhancements
Reveal indicator
In previous Versions, there was a little dot in the header of the Reveal Screen.
With the changes regarding the new iOS Look, this dot is now behind the “Networks” word.
It disappears, if the reveal is triggered.

Loading screen
If you start the Web App, there is now a “Loading…” Screen shown.
This has two reasons:
To have time to detect if there is an attack running without showing the PIN Entry Screen
To show, that the Web App is loading, and not only showing a white screen.
Faster Loading of the Web App
A lot of effort was made to speed up the loading of the Web App. It's now faster than ever.
The fastest loadings can be achieved with a kiosk browser (see below)


New Features
OTA - Over the Air Updates
With Version 5.3, we introduce OTA update possibility.
To use OTA you have to have at least Version 5.3 of the firmware installed. 
Download the latest release
Log into the Wi-Fi provided by the Hacker Device
Go to http://192.168.4.1/update
upload the bin File you want to install
There might be a "no Connection" error on the Screen. That's fine, the Wi-Fi will be gone because of the update.
After the upload, wait for the device to reboot (known by the vibration, which takes up to 1 minute)
You have to reconnect to the Wi-Fi.
If the Web App looks weird, please reload the page (close the Web App and reopen it)
Attack detection
Because there are Shortcuts and third party interactions now, there is a new feature.
If you open the Web App, there is a “Loading…” Screen.
While loading, the Web App checks, whether an attack is already running on the device or not. This could be triggered by a shortcut or the “send on start-up” feature, which is explained later.
If there is an attack running, the Web App will open the Reveal screen immediately.
From there you can peek the Word which is sending by touching the “AP table”. This is the Area with the Nearby Networks on the Screen.

You can then use the Reveal Screen and the Web App as in the previous Version.
Start the Reveal
Go back to the Pin Entry Screen and stop the sending
etc.

ATTENTION:
Make sure the Web App is closed (Task manager) before you open it, if you want to use this feature.

Attack detection while PIN Entry Screen is already opened
If you have the Web App started, before you trigger the sending of the Wi-Fi’s (either via Shortcut, “send on start-up” or third party app) you can click the “Cancel” Button.
If there is nothing to delete, the Web App will check, if the device sends Wi-Fi’s. If yes, it opens the Reveal Screen.
Update of the iPhone Reveal Screen
I changed the look of the Reveal Screen to match the new Wi-Fi Settings Screen of iOS. It’s not a perfect match, but nobody will notice.
You can change the wording for the two new texts in the settings via the Web App.
Start sending on start-up
If you want to force a word or card, it can be handy to have the possibility to send this without touching your phone.
You now can activate this feature in the settings and enter the Word that should be sent.
If active, the device will vibrate twice after the normal startup. (three times in sum)
This indicates, that the sending of the word has started.

You then are free to use the new Attack detection feature to reveal the word.
New API features
There are two new API handlers for third party integration. 
For more information, see the API documentation
Vibrate on API calls
To get noticed by the device, that an API call got received, you can enable “Vibrate on API calls” in the Settings of the Web App.
If active, the device will vibrate if an API call got received and was valid.
Settings Reset via Power cycle
If your device has problems with showing the Web App correctly, or other issues, you can try to do a factory reset.
All Settings will be deleted!
To do the factory reset, do the following:
Power off the device
Power on the device until it vibrates
Turn the device off immediately after the vibration
repeat these steps 3 times
on the 4 time, do not power off the device.
it will vibrate multiple times to let you know the factory reset worked.
Now check, if your problems are solved.
Settings Reset via Web App
In the Settings of the Web App, you can do Settings reset by clicking “Reset”.
Restart the device via Web App
In the Settings of the Web App, you can restart the device (to test “send on start-up” or after changing the Wi-Fi name) by clicking “Reboot Device”.

Reminder for Functions already there
Export of Settings and Words
At the bottom of the Settings and Words section in the Web App, you can export a JSON File.
For the Words file, this is handy, because you can edit it on your computer for your needs.
The Settings file can be used to restore your favorite Settings after installation of a new version.
Import of Settings and Words
At the bottom of the Settings and Words section in the Web App you can import a JSON File.
You can search for a file via the Button.
Importing Words
After clicking the import Button, the Import will start. It is finished when you can see your new Words in the list. The Saved Messages come a bit too early.
Importing Settings
After clicking the import Button, the Import will start. It is finished when the Saved Messages will come.

After importing, it might be that the PIN Entry will not work. Just restart your device.

Useful Hints
Use a Kiosk App
Chrome on Android and iOS is making full screen Web Apps harder and harder.
The best (and faster) way is to user a so-called kiosk browser.

iOS
Use Kiosk - fullscreen browser with the following Settings:



Android
Go to the Play Store and install Fully Kiosk Browser

https://play.google.com/store/apps/details?id=de.ozerov.fully

Open the Fully Kiosk Browser and set it up like this:


After connecting to your HACKER Network, you can start using Fully Kiosk browser.

To get the HACKER Icon on your Home Screen, open the Settings of Fully by swiping from the left and click “Add to Home Screen”.
Give it a name as you like.




Settings
General Settings



Device Name
The SSID the device will provide to connect to.
The Password will always be HACKER1234



Reveal Settings

Encrypted
The SSID('s) that will be sent are encrypted to look hacker like

Without dot
The SSID('s) that will be sent will not have the dot in front. The dot will sort the SSIDs at the beginning of the List of Wi-Fi's on the spectator's phone

Reveal Mode
If turned on this enables the 'Glitch' reveal whereby 

Reveal delay
The number of seconds after pressing the "Wi-Fi" section on the screen, before the glitch will start.
Reverse words for language
Will reverse the order of Suit and Value of the Card if that fits your language better.
Ex: "Queen of Hearts" will become "Hearts of Queen"

GUI Settings


iPhone or Android
Here you can change the look and feel of the Web GUI. You can choose between iPhone or Android general look.
Themes
There are 3 Themes you can choose. They change the Look of the “OIN Entry” Page
Activate Dark Mode
If enabled, the Revealscrren will have the look of the original Dark mode screens .

Special Features


Send Wi-Fi on Startup
If enabled, beacons will be sent when the device is started
Start SSID
The Wi-Fi Name to send if send Wi-Fi on Startup is enabled
Vibrate on API Calls
To get noticed by the device, that an API call got received, you can enable “Vibrate on API calls”.
If active, the device will vibrate if an API call got received and was valid.

API Reference
With Version 5 and above of the Firmware for HACKER the API has two new call functions:

To send a Text: 
http://192.168.4.1/send?word=”.Ace of Spades”
Possible responses:
200 → everything went well
422 → Word Parameter is missing or empty
409 → There is already an attack running

The word will be sent as it is. So the caller have to take care of the dot in front and encryption if needed.

To stop sending: 
http://192.168.4.1/stopSending
Possible responses:
200 → everything went well
409 → There is already no attack running

Check if device is sending:
http://192.168.4.1/isSending
Possible responses:
200 → everything went well, Response text is “true” if the device is sending and “false” if not


To stop sending: 
http://192.168.4.1/getSSIDgetSSID
Possible responses:
200 → everything went well, the response text contains the SSID including all the Whitespaces. You have to trim them like
 replace(/^[\s\u200B-\u200D\uFEFF]+|[\s\u200B-\u200D\uFEFF]+$/g, '');
409 → There is already no attack running

