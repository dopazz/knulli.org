# :material-controller: Custom Hotkey Shortcuts

!!! danger "Please read before getting started"

    The KNULLI team does **not** recommend customizing RetroArch hotkey shortcuts unless you are **absolutely sure** what you are doing. We **strongly** recommend getting familiar with the **global** [Hotkey Shortcuts](../../../play/hotkey-shortcuts) instead.
    
    Before you attempt to manually reassign your hotkey shortcuts in **RetroArch**, please be aware of two issues:

    * KNULLI comes with **a lot** of emulators which are **not** integrated with RetroArch. Your RetroArch settings will **not apply** to any **standalone emulators**. By changing your RetroArch shortcuts, you will put your device in an **inconsistent state** with **different shortcuts** for different emulators.
    * Some hotkey shortcut actions are implemented on the **operating system level**, not on the emulation level. Consequently, those hotkey shortcuts **cannot be disabled or modified** within RetroArch. Assigning any emulation-level action to a shortcut which is also assigned to an OS-level action will **inevitably** result in a **double binding**.

With every launch of a game, KNULLI re-generates RetroArch configuration files according to the settings you made in EmulationStation (the KNULLI GUI). Consequently, all settings you made in RetroArch while it was running will be reset the next time you launch a game.

If you want to set up your own custom RetroArch hotkey combinations, you have two options: You can use **overrides** to define hotkey combinations for each system or even game separately, or you can simply edit `batocera.conf` and set up your own hotkey bindings there.

## Creating system/game specific overrides

To have your in-game Hotkeys save across device reboots, you must save an **override** after editing the hotkeys themselves.  

**Overrides** can only save across (1) the specific game you're playing, (2) the content directory/folder that the game is loading from, or (3) the current game system core you are using.  This means that you will have to create new hotkey remaps for **at least** each game system (core) every time you want to permanently save your hotkey remapping. (This process is not complicated but can be tedious if done for each system at your device all at once.)

### Changing Hotkey Settings

To change your hotkeys for any game/folder/core, you must launch a game from the category that you wish you edit the hotkeys for.
Press the default Menu combination (++"Function"++ + :material-gamepad-circle-down:, or its equivalent, on most devices) to open the retroarch quick menu. Press B twice to jump to the menu that reads Main Menu, Settings, Netplay,... Enter the Settings menu and then enter the Input Menu.
Inside the Input menu enter the Hotkeys submenu.

**Be very careful when changing your hotkeys, at the very least make sure Hotkey Enable and Menu Toggle are buttons you can remember and not shared with any other combination.** This is in case you accidentally set any hotkey incorrectly and it causes future issues.

You can now scroll through all the hotkey functions and assign whichever buttons you like to work in conjunction with your "Hotkey Enable" button. I recommend going through the entire list and clearing out hotkeys that you do not plan to use to prevent accidentally duplicating button functions.

### Saving Hotkeys (via Overrides)

Now that your hotkeys are set to the buttons you desire, **you MUST save them into an override file** for them to not automatically be overwritten by emulation station whenever the device restarts.

To do this back out into the Main Menu screen (Main Menu, Settings, Netplay,...) then enter the first Main Menu option, and then the Quick Menu option.
Scroll near the bottom of the Quick Menu options (faster to just tap up to jump to the bottom) and enter the Overrides submenu.

Inside of Overrides, you can save your hotkey settings (and any other configurations you may have changed) to the specific **game** you have launched (not especially practical), the **folder** in which the game's rom file is located, or the **RetroArch core** that is playing the rom you have currently open.

It is likely that you'll want to save your override to the folder (Save Content Directory Overrides) or core (Save Core Overrides).  Once you save the override, you'll see a pop up notifying you  "Overrides saved successfully."

If your game is in a subfolder inside a ROMs folder (more likely in systems like PSX that may have multiple discs or split ROMs files), then you may want to save the override to the Core that typically launches your games for that system.  (Game Boy and Game Boy Color also tend to share a Core, so you can use this method to save your hotkeys across two systems in a case like this.)

If your games are all together in a shared ROMs folder (most common in the more retro systems whose roms are just 1 file), then you can save the override to the folder or the core.

This should be all you need to do to keep your hotkeys saved for each folder/core that you launch. You will have to repeat this process at the very least for each retroarch system that you use (unless they happen to share the same system emulation core).

Now whenever you open a game with a saved override, you should see a pop-up confirming that you have an override already saved to this current game and it has successfully launched.  If you change other settings in your retroarch menu (or re-do your hotkeys), it is possible that you must re-save your override file to keep your new changes as well.

## Set up hotkey bindings in `batocera.conf`

This approach is a little more advanced because you do need to know the keycodes of your controller to set up the mapping. But unlike the override method as described above, this is a global RA setting which needs to be set up only **once** without saving overrides.

In `batocera.conf`, you essentially add a block like this towards the end and bind the various RetroArch inputs to the hotkey button of your liking. You can use `"nul"` to disable actions you do not want to be assigned to a hotkey shortcut. You can find more detailed information about this approach in the [Batocera wiki](https://wiki.batocera.org/advanced_retroarch_settings#rebinding_retroarch_s_hotkeys).

```
# ------------ RA Overrides ----------- #
# --- Input Hotkeys --- #
global.retroarch.input_enable_hotkey_btn = "9"
global.retroarch.input_menu_toggle_btn = "6"
global.retroarch.input_exit_emulator_btn = "10"
global.retroarch.input_load_state_btn = "7"
global.retroarch.input_save_state_btn = "8"
global.retroarch.input_screenshot_btn = "3"
global.retroarch.input_toggle_fast_forward_btn = "14"
global.retroarch.input_rewind_btn = "nul"
global.retroarch.input_reset_btn = "nul"
global.retroarch.input_ai_service_btn = "nul"
global.retroarch.input_shader_prev_btn = "nul"
global.retroarch.input_shader_next_btn = "nul"
global.retroarch.input_state_slot_increase_btn = "nul"
global.retroarch.input_state_slot_decrease_btn = "nul"
global.retroarch.input_hold_fast_forward_btn = "nul"
```
