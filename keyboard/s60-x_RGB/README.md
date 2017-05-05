S60-X RGB keyboard firmware
===========================
DIY compact keyboard designed by VinnyCordeiro for Sentraq. Most of the keymaps are based on GH60 code.

## WARNING!!!
This is only for the RGB version of the S60-X and use QMK firmware for that.

## Hey, where is the code???
My coding skills are not very good, after 10+ years not programming professionaly. I was able to get around TMK, but QMK is confusing for me.

That said, [Ruiqi Mao](http://www.ruiqimao.com/) made (again!) an AMAZING job making [a site to create your own custom QMK firmware for your keyboard.](http://qmk.sized.io/) Just upload the proper JSON file and you'll have a basic setup already made, just leaving for you the finer details. ANSI and ISO files should be pretty straightforward; the GENERIC file just makes all keys available on the PCB visible, as some are not used on ANSI layout and others are not used on ISO layout, namely the extra keys for JIS and HHKB layout compatibility.

## But I really do prefer to code it directly!
That's ok. You can find the QMK firmware code [here](https://github.com/jbyoung/qmk_firmware), forked from the original repo.

## Build
Follow QMK firmware instructions, or download the HEX file directly from http://qmk.sized.io after you are finished setting up your keyboard.


## Flashing your keyboard
The recommended programs for flashing your keyboard are [Atmel FLIP](http://www.atmel.com/tools/FLIP.aspx) (Windows) and [dfu-programmer](http://dfu-programmer.sourceforge.net/) (Linux/Windows).

[QMK Firmware Flasher](https://github.com/jackhumbert/qmk_firmware_flasher/releases) may work, as the S60-X keyboard uses the ATMega32U4 microcontroller, but it is untested. Use at your own risk.


**Programming the firmware (Windows)**

1. download and install FLIP (http://www.atmel.com/tools/FLIP.aspx)
2. connect the keyboard, press the program button (S1) and wait until it enumerates
3. go to device manager, find the atmega32u4 chip and click "update driver"
4. choose location manually: folder named "usb" inside the installation directory of FLIP
5. once the driver is installed, run flip
6. Device -> Select: choose ATMega32U4
7. Settings -> Communication -> USB, FLIP should show the signature at this point (58 1E 95 87)
8. File -> Load HEX file: choose the hex firmware: <firmware>.hex
9. click "Run"
10. after programming is done, disconnect the device from USB and connect again.


**Programming the firmware (Linux)**

1. Download and install/compile/unpack dfu-programmer from http://dfu-programmer.sourceforge.net/.
2. Issue the following commands in the command prompt after connecting the device and pressing the programming button (S1). You may need root permissions or udev rules to do that.
  1. `sudo dfu-programmer atmega32u4 erase`
  2. `sudo dfu-programmer atmega32u4 flash <firmware>.hex`
  3. `sudo dfu-programmer atmega32u4 start`
3. The keyboard should start working. If it doesn't, reconnect the cable.


### 0  Initial explanations
The keymaps bellow are the ones available in the GH60 keyboard. The S60-X RGB can replicate all of them, but I don't have the time anymore to code them. I'll leave that as suggestions for the user to program them at http://qmk.sized.io

The █████ blocks on the layouts hides the switch positions that do not exist physically on the PCB. If you feel like hacking the keyboard and adding new keys, those are the positions that can be used.

The ▒▒▒▒▒ blocks hides switch positions not used on this particular layout, but they do exist on the PCB.


### 1  Standard - ANSI

#### 1.0 Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ ESC │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │▒▒▒▒▒│BKSPC│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ TAB │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │  \  │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │CAPSL│  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │  ;  │  '  │▒▒▒▒▒│ENTER│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │LSHFT│▒▒▒▒▒│  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │▒▒▒▒▒│RSHFT│▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │LCTRL│L_GUI│L_ALT│█████│█████│█████│ SPC │█████│█████│█████│R_ALT│ FN0 │ APP │RCTRL│█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘
#### 1.1 Fn layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │GRAVE│ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │▒▒▒▒▒│     │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │ Up  │     │     │     │     │     │PGUP │PGDWN│PRTSC│SCLCK│PAUSE│     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │Left │Down │Right│     │     │     │     │     │     │     │     │▒▒▒▒▒│     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │▒▒▒▒▒│     │     │     │     │     │     │     │     │     │     │▒▒▒▒▒│     │▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │█████│█████│█████│     │█████│█████│█████│     │     │     │     │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘


### 2  Standard - ISO
The same as the standard keymap, but with additional ISO keys.


#### 2.0 Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ ESC │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │▒▒▒▒▒│BKSPC│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ TAB │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │▒▒▒▒▒│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │CAPSL│  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │  ;  │  '  │NUHS │ENTER│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │LSHFT│  \  │  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │▒▒▒▒▒│RSHFT│▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │LCTRL│L_GUI│L_ALT│█████│█████│█████│ SPC │█████│█████│█████│R_ALT│ FN0 │ APP │RCTRL│█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘
#### 2.1 Fn layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │GRAVE│ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │▒▒▒▒▒│     │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │ Up  │     │     │     │     │     │PGUP │PGDWN│PRTSC│SCLCK│PAUSE│▒▒▒▒▒│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │Left │Down │Right│     │     │     │     │     │     │     │     │     │     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │     │     │     │     │     │     │     │     │     │▒▒▒▒▒│     │▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │█████│█████│█████│     │█████│█████│█████│     │     │     │     │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘

    
### 3  Poker
Emulates original Poker layers.

    Fn + Esc = `
    Fn + {left, down, up, right}  = {home, pgdown, pgup, end}

#### 3.0 Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │  `  │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │▒▒▒▒▒│BkSpc│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ Tab │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │  \  │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Caps │  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │  ;  │  '  │▒▒▒▒▒│Enter│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Shift│▒▒▒▒▒│  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │▒▒▒▒▒│Shift│▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Ctrl │ Gui │ Alt │█████│█████│█████│Space│█████│█████│█████│ Fn  │ Gui │ App │Ctrl │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘
#### 3.1 Poker Fn layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ Esc │ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │▒▒▒▒▒│     │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │ FnQ │ Up  │     │     │     │     │     │     │ Cal │     │Home │ Ins │     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │Left │Down │Right│     │     │ Psc │ Slk │Pause│     │ Tsk │ End │▒▒▒▒▒│     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │▒▒▒▒▒│ Del │     │ Web │Mute │ VoU │ VoD │     │PgUp │PgDwn│ Del │▒▒▒▒▒│ Up  │▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │█████│█████│█████│ FnS │█████│█████│█████│ Fn  │Left │Down │Right│█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘


### 4. Plain
Without any Fn layer this will be useful if you want to use key remapping tool like AHK on host.

#### 4.0 Plain Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ Esc │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │▒▒▒▒▒│BkSpc│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ Tab │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │  \  │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Caps │  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │  ;  │  '  │▒▒▒▒▒│Enter│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Shift│▒▒▒▒▒│  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │▒▒▒▒▒│Shift│▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Ctrl │ Gui │ Alt │█████│█████│█████│Space│█████│█████│█████│ Alt │ Gui │ App │Ctrl │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘


### 5. Hasu
This is Hasu's favorite keymap with HHKB Fn, Vi cursor and Mousekey layer.

(Hasu is the creator of the TMK firmware, for those who do not know that.)


### 6. SpaceFN
This layout proposed by spiceBar uses space bar to change layer with using Dual role key technique. See [SpaceFN discussion](http://geekhack.org/index.php?topic=51069.0).

#### 6.0 Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ Esc │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │▒▒▒▒▒│BkSpc│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ Tab │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │  \  │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Caps │  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │  ;  │  '  │▒▒▒▒▒│Enter│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Shift│▒▒▒▒▒│  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │▒▒▒▒▒│Shift│▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Ctrl │ Gui │ Alt │█████│█████│████ Space/Fn ███│█████│█████│ Alt │ Gui │ App │Ctrl │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘
#### 6.1 SpaceFN layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │  `  │ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │▒▒▒▒▒│ Del │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │     │     │     │     │Home │ Up  │ End │ Psc │ Slk │Pause│ Ins │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │     │     │     │PgUp │Left │Down │Right│     │     │▒▒▒▒▒│     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │▒▒▒▒▒│     │     │     │     │Space│PgDwn│  `  │  ~  │     │     │▒▒▒▒▒│     │▒▒▒▒▒│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │     │     │█████│█████│█████│ Fn  │█████│█████│█████│ Alt │ Gui │ App │Ctrl │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘


### 7. HHKB
Emulates original HHKB layers.
#### 7.0: Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ Esc │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │  \  │  `  │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ Tab │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │BkSpc│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Ctrl │  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │ Fn3 │  '  │▒▒▒▒▒│Enter│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Shift│▒▒▒▒▒│  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │▒▒▒▒▒│Shift│ Fn  │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │▒▒▒▒▒│ Gui │ Alt │█████│█████│█████│Space│█████│█████│█████│▒▒▒▒▒│ Alt │ Gui │▒▒▒▒▒│█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘
#### 7.1: HHKB Fn layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │ Pwr │ F1  │ F2  │ F3  │ F4  │ F5  │ F6  │ F7  │ F8  │ F9  │ F10 │ F11 │ F12 │ Ins │ Del │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Caps │     │     │     │     │     │     │     │ Psc │ Slk │ Pus │ Up  │     │     │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │ VoD │ VoU │ Mut │ Ejc │     │  *  │  /  │Home │PgUp │Left │Right│▒▒▒▒▒│Enter│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │     │▒▒▒▒▒│     │     │     │     │     │  +  │  -  │ End │PgDwn│Down │▒▒▒▒▒│     │     │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │▒▒▒▒▒│     │     │█████│█████│█████│     │█████│█████│█████│▒▒▒▒▒│     │     │▒▒▒▒▒│█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘

    
### 8  Custom
The custom keymap is where I tested all the switches, not being concerned with a specific layout or layers. It's a plain layout option with the extra keys used on ISO & HHKB layouts being assigned some other keys.

#### 8.0 Default layer
    ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐
    │  `  │  1  │  2  │  3  │  4  │  5  │  6  │  7  │  8  │  9  │  0  │  -  │  =  │PgUp │BkSpc│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │ Tab │  Q  │  W  │  E  │  R  │  T  │  Y  │  U  │  I  │  O  │  P  │  [  │  ]  │  \  │█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Caps │  A  │  S  │  D  │  F  │  G  │  H  │  J  │  K  │  L  │  ;  │  '  │PgDwn│Enter│█████│
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Shift│Home │  Z  │  X  │  C  │  V  │  B  │  N  │  M  │  ,  │  .  │  /  │ End │Shift│  Up │
    ├─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
    │Ctrl │ Gui │ Alt │█████│█████│█████│Space│█████│█████│█████│ Alt │ Gui │ App │Ctrl │█████│
    └─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘

