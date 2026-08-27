This is my log of the work I put into this project, with an estimate of how much time I spent on each step!

### Making the Schematic (3.5hr)
I started making the schematic by referring to the RP2040 Hardware design docs, as well as the docs for the Radio Module 2 and some of the other stuff I used. Most of this time was spent back and forth reading docs, picking ICs and figuring it out. I guess at one point, that's just how all PCBs work huh.

The RP2040 is pretty standard stuff, give it 3.3V, a decent QSPI flash chip and decoupling and it works like a charm. The Radio Module 2 was a bit interesting, but I just ended up following what the docs did word for word, wireless is something I really don't wanna fuck around and find out :/

The Buck/Boost is fun! I put in a TI TPS63001, which gives a nice 3v3 voltage with minimal stuff! I added 2 diodes to prevent backfeeding into USB or the battery, and installed a TP4056 in conjunction with everything else.
![schem](assets/schem.png)

### Starting the PCB (2.5hr)
By this point, making this PCB was quite straightforward as well. I placed all the components and added the components. I shifted the USB C and main mcu to the left side, and the wireless stuff to the right solely because I wanted to keep both on an edge and it would look awkward and unbalanced all together. Routing is pretty easy too. The only things that needed some focus was the USB Differential pair and the QSPI length matching. I got the radio module lengths down to a 10mm difference, which isn't that good but it should be alright :p. I might fix that later though.
![PCB1](assets/pcb1.png)

### Silkscreen! (2hr)
As a ruler, I wanted to pack as many cool units/measurements into the design of it! So, I spent a while finding the best units to put on it while staying practical and hacky. I settled on the Parsec (or at least a quntillionth), 100 light picoseconds (1 was too small, and a nanosecond was too large), and 1 trillionth of an Astronomical Unit (that's the distance from the earth to the sun*) (*t&c apply). I also added the wavelengths (and quarter waves) of the wifi and bluetooth onboard (2.4GHz) and then 5GHz Wifi too.

I also finally added the ticks to the scale of the ruler. For the metric side, I just put a tick every 1mm, and then every 0.02 inches on the imperial side.
I also then added a length conversion table!
<img width="1588" height="262" alt="image" src="https://github.com/user-attachments/assets/69d51fac-a8ff-42ff-b087-11bd8fecd9e2" />
<img width="1578" height="260" alt="image" src="https://github.com/user-attachments/assets/3b9d18c1-2338-4583-935d-f19f590f55ec" />

### PCB fixes (2hr)
I then ran DRC a few times, fixed my mismatched trace widths, ran DRC, fixed more stuff, etc. I also ended up redoing the signal routing for the radio module chip, since I guess the length matching was real bad. This time around, I got it down to less than 1mm on a 175mm routed length! I also changed the hole footprints on the heat pads of the buck-boost and charging module because hole size limitations. 
<img width="1579" height="250" alt="image" src="https://github.com/user-attachments/assets/1bc6fc9d-3b4f-475e-9859-b5d930b9bca7" />
<img width="856" height="349" alt="image" src="https://github.com/user-attachments/assets/772cd03f-8106-4ad8-b91f-bbdde7e3c2e8" />
<img width="846" height="704" alt="image" src="https://github.com/user-attachments/assets/36873c19-c4c2-484d-a16d-9b8bc6e6d0c7" />

Using the empty space I had, it was a nice idea to add a few buttons and LEDs, so I added 4 WS2812B 5050 LEDs and 3 buttons! Fortunately, no more DRC errors from this addition, but the Edge cuts were malformed (classic edge cuts). Fixed those, and I should be done now!

After this, I also added a reset button, since I am already adding like 4 buttons for the GPIO and boot selection :p
<img width="733" height="313" alt="image" src="https://github.com/user-attachments/assets/ec9e8d0e-8fb3-4d09-af52-5926c9a31954" />

I worked on this repo for an hour after this, and I have now completed this project! 


You can find the final PCB, schematic and design in the README

<img width="1675" height="312" alt="image" src="https://github.com/user-attachments/assets/22875b05-3b50-4c5c-8c15-5fef0ebb3259" />
