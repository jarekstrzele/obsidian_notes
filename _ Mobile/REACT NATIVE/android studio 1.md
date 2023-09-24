# Androidstudio

TO STOP EMULATOR
1. open a terminal window (either the AS one or any other, as long as `adb` commands are available)
2. list the running connected devices with: `adb devices`
3. identify your emulator in the resulting list (usually in the form of: emulator-5556    device)
4. now kill the emulator with: `adb -s emulator-5556 emu kill` (replace the name of your own emulator in the command of course)

You'll see a confirmation message like OK: killing emulator, bye bye






