AUNK Numpad keyboard firmware
=============================
Made to transform the NPKC 17 Switch Tester (https://www.massdrop.com/buy/npkc-switch-tester?mode=guest_open or https://www.massdrop.com/buy/npkc-17-switch-tester?mode=guest_open) into a fully operational numpad. The PCB can be bought here: http://dirtypcbs.com/view.php?share=14162&accesskey=f429cad9a82d1292b1013e43a49ba001

Be warned that the design is untested. I'm considering open sourcing it in the near future, as I don't have the time right now to debug my non-working prototype.

## Build
Move to this directory then just run `make` like:

    $ make

I have deleted the option to use PJRC stack, there's no reason to use it.


## Keymap
The keymap is programmed to be a simple, vanilla numpad. Obviouly you are free to make modifications yourself. I recommend studying the source code of the GH60 for that. Or visit the amazing tutorial that matt3o have made: http://deskthority.net/workshop-f7/how-to-build-your-very-own-keyboard-firmware-t7177.html
