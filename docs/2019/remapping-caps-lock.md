# Remapping caps lock

---

#### Overview

Print current modifiers with `xmodmap`:

    xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

    shift       Shift_L (0x32),  Shift_R (0x3e)
    lock        Caps_Lock (0x42)
    control     Control_L (0x25),  Control_R (0x69)
    mod1        Alt_L (0x40),  Meta_L (0xcd)
    mod2        Num_Lock (0x4d)
    mod3      
    mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
    mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)


To disable caps lock enitrely:

    $ xmodmap -e "clear Lock"


---


#### Using an .Xmodmap file

Some configurations require multiple commands to `xmodmap`. To make this easier we can define a file for `xmodmap` to read each time you log into your OS.

For example, let's make <kbd>hyper</kbd> available to us by mapping it to the now-available <kbd>caps lock</kbd> key.

Add the following to a file at `~/.Xmodmap` :

    ! First, Unmap capslock
    clear Lock
    
    ! `66` is the code sent from the keyboard to the OS by the actual `caps lock` key
    
    ! Next, Label `caps lock` key as `Hyper`
    keycode 66 = Hyper_L
    
    ! Leave mod4 as Super *only*
    remove mod4 = Hyper_L
    
    ! Set mod3 to `caps lock` = `Hyper` key
    add mod3 = Hyper_L
    
Execute with `$ xmodmap ~/.Xmodmap`, then check the state of the modifiers:

    xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):
    
    shift       Shift_L (0x32),  Shift_R (0x3e)
    lock      
    control     Control_L (0x25),  Control_R (0x69)
    mod1        Alt_L (0x40),  Meta_L (0xcd)
    mod2        Num_Lock (0x4d)
    mod3        Hyper_L (0x42),  Hyper_L (0xcf)
    mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce)
    mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)
    

Hooray! More chords for Emacs fun.


---

#### Alternate ways of enabling Caps Lock

Toggle caps by pressing both left and right <kbd>shift</kbd> keys:

    $ setxkbmap -option "shift:both_capslock"


---

#### Links

- https://www.howtogeek.com/194705/how-to-disable-or-reassign-the-caps-lock-key-on-any-operating-system/
- https://medium.com/@damko/a-simple-humble-but-comprehensive-guide-to-xkb-for-linux-6f1ad5e13450

<br>


