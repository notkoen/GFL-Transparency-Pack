
# GFL Transparency Materials

(Last updated: <t:1675966721:F>)

Repository dedicated to publicly storing my edits to GFL CS:GO ZE's transparent models pack found on the forums.

## Credits & Thanks

- Potti: For creating the first transparent models
- Vauff: For updating and maintaining the download files
- Ice/FrozenH20: For creating the adjustable proxies

# Installation

1. Pick which pack you want to install:
    - `Standard` - Players fade slowly and are less transparent
    - `Strong` - Players fade instantly and are more transparent
    - `Adjustable` - Adjustable player fade and transparency

2. Copy the `materials` folder in the pack of your choice to `%yoursteamlocation%\steamapps\common\Counter-Strike Global Offensive\csgo`
    - *IF YOU WERE NOT PROMPTED TO REPLACE FILES, YOU DID NOT COPY INTO THE RIGHT FOLDER (or you've never played on the server before?)*
    - If you are not using the `Adjustable` transparency pack, then you are all set! If you are, continue below

3. Go to your cfg folder @ `%yoursteamlocation%\steamapps\common\Counter-Strike Global Offensive\csgo\cfg` and look
for a file named `autoexec.cfg` *(not all players have it. If not there, just create a new .cfg file and name it autoexec.cfg)*

4. Add the following lines to your autoexec config file. It is **crucial** that you put this in your autoexec file

    ```yaml
    // Create fake cvar for hide distance
    setinfo hide_dist 0.5 // -1 = Disable, higher number = larger range

    // Bind "z" key to toggle hide distances
    bind z "hideToggle"

    // Toggle script
    alias "hideToggle" "hideOn"
    alias "hideOn" "setinfo hide_dist 999; alias hideToggle hideMed"  // Full hide
    alias "hideMed" "setinfo hide_dist 1.5; alias hideToggle hideOff" // Close range transparency
    alias "hideOff" "setinfo hide_dist -1; alias hideToggle hideOn"   // Transparency disabled
    ```

5. Open steam library, right click on CSGO, press properties and add `+exec autoexec.cfg` to your
launch option

If you followed all the steps correctly, just load into GFL and press "Z" (or whatever key you set it to) and it should automatically
cycle through all the hide modes.

## Customization

- Change `bind z "hideToggle"` to the key you prefer to use

- Normal transparency range can be set by changing the number to between `0.5` to `5.0`:
  - `alias "hideMed" "setinfo hide_dist <DESIRED DISTANCE>; alias hideToggle hideOff"`

- To have it toggle between hide enabled and disabled, replace the 3 aliases under `// Toggle script` to these lines:

     ```yaml
    alias "hideOn" "setinfo hide_dist 999; alias hideToggle hideOff" // Full hide
    alias "hideOff" "setinfo hide_dist -1; alias hideToggle hideOn"  // Transparency disabled
    ```

## Help & Support

If you need help and/or assistance, feel free to ping me in `#ze-chat` in GFL CS:GO ZE's [Discord Server](https://discord.gg/Bkfwg4q) or submit an issue in this repository.
