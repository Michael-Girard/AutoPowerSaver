# AutoPowerOptions
Switches between two Windows Power Options settings based on activity.

The program, which resides in the system tray, tracks the location of the mouse arrow. It polls once per second. It records the mouse position with each poll, and if the position is the same between polls, a counter is incremented (else it's reset). Once a certain threshold is reached on the counter, the program silently switches from one setting to another by running a command line command.

Once the program detects mouse movement again after switching Power Options settings, it switches back to the other setting.

The default threshold is 20 minutes, so 1200 poll cycles.

The program resides in the system tray and the threshold duration can be modified to a number of different values by right clicking on the icon and selecting the new value. Goes as low as 5 minutes and as high as 60 minutes (5, 10, 15, 20, 30, 60). It does not currently accept custom values.

~~Due to how the GUIDs for power options can vary on some systems, this program isn't guaranteed to work on everyone's computers. To be certain, you must identify your GUIDs and replace the FINAL strings with them.~~ The program is currently set to swap to High Performance when activity is detected and Power Saving when activity is not detected. ~~This can be modified at the bottom of the code by swapping in the correct GUIDs/FINAL strings in the main method.~~

The Java_Icon.png should be in the same directory as the program, otherwise an exception will occur and the program will run with no icon in the system tray. The .jar file has it built in.

Update January 23rd, 2017
-----
-Changed the name to AutoPowerSaver and modified the code to reflect that.

-Changed GUID variables to not be final.

-Modified the batch names to be more generic.

-Added getGUIDs() method that...

---Runs powercfg /list

---Reads the resulting GUID list into a StringBuilder

---Uses substring() and indexOf() methods to extract the Power Saver and High Performance GUIDs

---Assigns those GUIDs to the GUID variables

---In short, makes the program work with all systems without going through the hassle of modifying the code with the GUIDs manually.
