# BigSaltyKeyboard-65ROL
A 65% Keyboard with a rotary encoder, OLED screen and LEDs


## Journal
You can visit the `./Photos` folder to find pictures related to each devlog!  
### Devlog 1:
Behold, the start of the project!
I do not have much experiance making keyboards but have been thinking of building one for a lil bit now, and once I came across Keeb it seemed like a great opportunity!  
I kicked this project off with a bit of planning and I present to you the overview of my custom keyboard:  
- Main Board:  
The BigSaltyKeyboard will be a 65% keyboard, meaning it will contain the primary keys + the 4 arrow keys + 4 nav keys: Del, Ins, Pup, and Pdn. I chose this layout as I really enjoy the smallness of 60%s but I certain games I play require the use of the arrows and being able to use the nav keys really helps typing flow. 
The keys will also be a bit offset from each other in the standard way most keyboards do simply for the ergonomics.

- Extra Spice:  
My keyboard will have a few hardware and software features that bring it's uniquness to life! First of all every key will have an SK6812 Mini-E LED under it to add some flare and animations! The top of the keybaord will have a small panel extending upwards containing some cool extra features, mainly a 0.91in programmable OLED screen and a rotary encoder that will be dedicated to volume control! It will also contain some small buttons that can br programmed to do whatever you please!

PCB Design:  
I begun the project by starting the schematic for the PCB in KiCad! For now all I have are ~68 keys connected to diodes for the key matrix and labeled onto the Pico! Due to the nature of the project it will need 2 PCB's, one for the board and another for the extended top, but for now ill work only on the board. 

Next Up:
1. Link footprints and but together PCB with keys
2. LEDs
