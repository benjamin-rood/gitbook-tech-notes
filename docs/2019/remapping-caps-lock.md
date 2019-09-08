# Remapping caps lock

---

## Overview

Print current modifiers with `xmodmap`:

    xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

    shift       Shift_L (0x32),  Shift_R (0x3e)
    lock      
    control     Control_L (0x25),  Control_R (0x69)
    mod1        Alt_L (0x40),  Meta_L (0xcd)
    mod2        Num_Lock (0x4d)
    mod3      
    mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
    mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

    

Clear caps lock enitrely:

    xmodmap -e "clear Lock"


## Using an .Xmodmap file

Some configurations require multiple commands to `xmodmap`. To make this easier we can define a file for `xmodmap` to read each time you log into your OS.

#### Example: Mapping <kbd>Hyper</kbd> to <kbd>Caps Lock</kbd> 

Add the following to a file at `~/.Xmodmap` :

    ! Unmap capslock
    clear Lock
    
    ! Label `caps lock` key as `Hyper`
    keycode 66 = Hyper_L # 66 is the keycode for the actual `caps lock` key
    
    ! Leave mod4 as Super *only*
    remove mod4 = Hyper_L
    
    ! Set mod3 to `caps lock` = `Hyper` key
    add mod3 = Hyper_L
    
Execute with `xmodmap ~/.Xmodmap`


## Caps without the 'caps lock' key

Toggle caps by pressing both left and right <kbd>Shift</kbd> keys:

    setxkbmap -option "shift:both_capslock"






