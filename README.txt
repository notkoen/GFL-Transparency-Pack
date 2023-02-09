#####################################################
# Proxies by Ice, Edited by Koen (Update 6/18/2022)
# Contact me notkoen#4977 if you need help
#####################################################

###############
# Installation
###############

1) Copy the "materials" folder in the pack to "%yoursteamlocation%\steamapps\common\Counter-Strike Global Offensive\csgo"

*IF YOU WERE NOT PROMPTED TO REPLACE FILES, YOU DID NOT COPY INTO THE RIGHT FOLDER (or you've never played on the server before?)*

2) Next up, you want to go to your cfg folder @ "%yoursteamlocation%\steamapps\common\Counter-Strike Global Offensive\csgo\cfg" and look 
for a file named "autoexec.cfg" (not all players have it. If not there, just create a new .cfg file and name it autoexec.cfg)

3) You want to add the following lines to your autoexec config file. It is crucial that you put this in your autoexec file as the actual
hide toggle part relies on this.

///////////////////////////////////////////
//GFL toggle hide via transparency alias

setinfo hide_dist 0.5 //create fake cvar for hide distance
                      //the number is the distance, -1 disables transparency, higher number means larger range

bind z "hideToggle"   //sets z to the button for the transparency toggles, *YOU CAN EDIT IT YOURSELF*

alias "hideToggle"   "hideOn"
alias "hideOn"       "setinfo hide_dist 999; alias hideToggle hideMed" //full hide 
alias "hideMed"      "setinfo hide_dist 1.5; alias hideToggle hideOff" //close range transparency
alias "hideOff"      "setinfo hide_dist -1; alias hideToggle hideOn"   //transparency disabled
////////////////////////////////////////////


4) Open your steam library and right click on csgo, press properties and then modify launch options. Add "+exec autoexec.cfg" to your
launch option so it always executes autoexec.cfg when starting your game so the aliases are stored/loaded.

5) If you followed all the steps correctly, just load into GFL and press "Z" (or whatever key you set it to) and it should automatically
cycle through all the hide modes

################
# Customization
################
1) You can change "bind z "hideToggle"" to whatever key you want

2) You can modify the range of the normal transparency by setting this number to between 0.5 to 5.0:

alias "hideMed"      "setinfo hide_dist 1.5; alias hideToggle hideOff"

3) If you want to have it just toggle between 2 modes (!hide / no !hide) then just replace the 3 aliases with these 2 aliases:
///////////////////////////////
alias "hideOn"       "setinfo hide_dist 999; alias hideToggle hideOff" //full hide 
alias "hideOff"      "setinfo hide_dist -1; alias hideToggle hideOn"   //transparency disabled
///////////////////////////////
