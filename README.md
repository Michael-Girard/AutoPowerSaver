# AutoPowerOptions
Switches between two Windows Power Options settings based on activity.

The program, which resides in the system tray, tracks the location of the mouse arrow. It polls once per second. It records the mouse position with each poll, and if the position is the same between polls, a counter is incremented (else it's reset). Once a certain threshold is reached on the counter, the program silently switches from one setting to another by running a command line command.

Once the program detects mouse movement again after switching Power Options settings, it switches back to the other setting.

The default threshold is 20 minutes, so 1200 poll cycles.

The program resides in the system tray and the threshold duration can be modified to a number of different values by right clicking on the icon and selecting the new value. Goes as low as 5 minutes and as high as 60 minutes. It does not currently accept custom values.

Due to the requirement of knowing the GUID for each Power Options settings, which vary from system to system, the current program only works on my system. To get it working on yours, you must identify your GUIDs and replace the FINAL strings with them. The program is currently set to swap to High Performance when activity is detected and Power Saving when activity is not detected. This can be modified at the bottom of the code by swapping in the correct GUIDs/FINAL strings at the Runtime.getRuntime().exec() methods.