# BigSaltyKeyboard-65ROL
A 65% Keyboard with a rotary encoder, OLED screen and LEDs


## BOM:

- 1x Raspberry Pi Pico
- 68x Cheery MX Switches and their keycaps
- 68x [1N4148 Through-Hole Diodes](https://www.digikey.ca/en/products/detail/onsemi/1N4148/458603)
- 1x 6.25u Stabilizer
- 2x 2.25u Stabilizer
- 1x 2u Stabilizer
- 68x [SK6812 MINI-E LEDs](https://www.lcsc.com/product-detail/C5149201.html)
- 1x [Logic Level Shifter](https://www.digikey.ca/en/products/detail/texas-instruments/SN74AHCT1G125DBVR/376028)
- 69x [0.1 µF Chip Capacitor](https://www.digikey.ca/en/products/detail/samsung-electro-mechanics/CL10E104KC8VPNC/20498486)
- 1x [500 OHM Chip Resistor](https://www.digikey.ca/en/products/detail/yageo/RT0603BRC07500RL/7708292)

## Journal
You can visit the `./Photos` folder to find pictures related to each devlog!  
### Devlog 1: 3 hours
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

<img src="https://github.com/LRGuess/BigSaltyKeyboard-65ROL/blob/main/Photos/Devlog1-Schematic.png" 
     alt="Devlog1 Image"
     width="600"
     height="500"> 

### Devlog 2: 3 hours
After having finished the key's schematic layout for the base PCB I dedcided the next step was to lay the keys out on the PCB! My current keyboard is an ATK RS6, and I'm quite used to it's layout and spacing so I decided I would replicate it with a small tweak: I made the left control key just a little bit larger so that I don't have to extend my thumb as far as I do on my current one. Honestly, spacing the keys out was kinda hard but it was a great learning opportunity, and figuring out how to place the stabalizers was also fun to figure out.  
Something I did to help figure the proper spacing out was downloading the CAD for an MX key and a keycap for the switch footprint so I could visualize the spacing in the 3D tool! At first I got the switch CAD to import no problem, but as soon as I tried to import the keycap it wouldn't show up. Long story short, for some ungodly reason KiCAD didn't like the keycap's CAD to be in an STL format but after a conversion to STP everything went smoothly. 

Next Up:
1. Place diodes, Pico, and define board edge.
2. LEDs

<img src="https://github.com/LRGuess/BigSaltyKeyboard-65ROL/blob/main/Photos/Devlog2-PCB%20KeyLayout.png" 
     alt="Devlog2 Image"
     width="600"
     height="500"> 

### Devlog 3: 4 hours
Right off the bat this part took a lot longer than I thought it would. Manually trying to drag every single diode to the right position was an absolute nightmare they're so small it's literally aim trainging of some sorts. Holy cow. 
Anyways, after placing every diode I decided to place the Pico right above the entire structure. Yes this adds a lot of space but that space will be right under the extention and I do need a spot to place the connectors to the other PDB. I'll get into that more in the next devlog.
The last thing I did was define the board's outlines and add a ground fill. I'm leaving about 2.4mm of space between the edge of the board and the switches, which I think will be enough for a sandwitch fit case. Running the DRC nothing failed so all is well with the board for now!

Next Up:
1. LEDs
2. Plan 2nd board connection

<img src="https://github.com/LRGuess/BigSaltyKeyboard-65ROL/blob/main/Photos/Devlog3-Board.png" 
     alt="Devlog3 Image"
     width="600"
     height="500"> 

### Devlog 4: 7 hours
Oh boy this one was fun. I really want my keyboard to have LEDs under each key, overall I think it adds a lot of character and improves the overall look of the board. Also they're lowkey aura.  
First thing's first I created a schematic in KiCad and mapped out the routes the data lines were going to take. To make routing a lot easier, I decided that every 2nd row of LEDs are going to be turned upside down, making the data line not have to cross the entire board to start a new row of LEDs. This bit was easy enough and after assigning all the footprints I got to work routing. Now I have routed LEDs in the past, and the process of placing the LEDs got a bit repetitive, so we'll skip to the start of the problems.  
After I finished routing the LEDs I tried to preform a DRC. For some ungodly reason 9/10 times I tried KiCad would crash, never giving me the results. Now I can't really skip over this because there is no way I made a perfect board, so for a few hours it was literally just brute forcing KiCad until it decided to give me the DRC results. At the end of the day it was not too bad as all I had to do was add some vias to allow all the ground fill islands to connect to each other and provide thermal relief. 

Next Up:
1. Create 2nd Schematic for rear extention
2. Figure out how to connect the 2nd PCB to the Pico


<img src="https://github.com/LRGuess/BigSaltyKeyboard-65ROL/blob/main/Photos/Devlog4-LEDsSchem.png" 
     alt="Devlog3 Image"
     width="600"
     height="500"> 
<img src="https://github.com/LRGuess/BigSaltyKeyboard-65ROL/blob/main/Photos/Devlog4-LEDsBoard.png" 
     alt="Devlog3 Image"
     width="600"
     height="500"> 

### Devlog 5: 2 Hours
I recently shared my keyboard design with the community, and I got a few comments about the LEDs. There were a few changes I needed to make to ensure the LEDs would work properly:
1. Every LED needs a decoupling capacitor to prevent high frequency noise from messing with the LEDs.
2. The LEDs data lines read HIGH from a 5v pin, but the Pico's data lines are 3.3v. Due to this I needed to insert a logic-level shifter between the Pico and the first LED.
3. After the Logic Level shifter it is also recommended to insert a 500OHM resistor on the data line.

After about an hour of research I figured out what components to use and placed them all on the schematic!

Next Up:
1. Place all new components on PCB
2. 2nd PCB

<img src="https://github.com/LRGuess/BigSaltyKeyboard-65ROL/blob/main/Photos/Devlog5.png" 
     alt="Devlog3 Image"
     width="600"
     height="500"> 
