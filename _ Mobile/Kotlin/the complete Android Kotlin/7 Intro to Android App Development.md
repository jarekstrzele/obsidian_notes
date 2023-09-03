[[_ the complete Android Kotlin]]

A NEW PROJECT -- ==wait until your project will be finished==
- verify: the emulator technology is active?
	- Task manager > Performance tab (Virtualisation: Enabled)
	- https://developer.android.com/studio/run/emulator-acceleration
- start a virtual device
	- on the top there is a phone icon (*Device Manager*/ *AVD Manager*) or from *Tools*
		- or Android SDK (Android 11.0) ; choose with *play* icon
- if you have no *res/activity_main.xml*, to 
	- samodzielnie w `res` Directory `layout` > *new* -> *layout resource file* add the name `activity_main`
	- or *File* > *Invalidate Caches / Restart*


----
>Enabling Virtualization (VT-x or AMD-V, SVM) in BIOS

> NOTE: If virtualization technology is enabled on your computer or you have successfully installed the emulator, ignore the explanations here.

As I mentioned in the previous lesson, if virtualization technology is not enabled on your computer, you must enable it in order to use the emulator.

If you’re using an Intel processor, then you have to enable **VT-x** or **VT-d** from the BIOS of your computer.

To do so, restart your computer and open the BIOS menu. This can usually be done by pressing the **delete** key, the **F1**, **F10** key or **Alt** and **F4** keys depending on the system.

The BIOS settings for Asus computer users are as follows.

1. Turn **ON** the System.
    
2. Press the **F2** key at startup BIOS Setup.
    
3. Press the right arrow key to the **Advanced** tab, Select **Virtualization Technology** and then press the **Enter** key.
    
4. Select **Enabled** and press the **Enter** key.
    
5. Press the **F10** key and select **Yes** and press the **Enter** key to save changes and **Reboot** into Windows.
    

If the manufacturer of the computer or CPU you use is different, you can find out how to do this in the BIOS with a quick google search.







