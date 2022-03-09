<div align="right"><i>Year: 2018</i></div>
<img src="https://user-images.githubusercontent.com/32619706/149883709-d17ce99c-5617-4dc2-a492-fd3b590a5fdc.png">
Designed, fabricated and programmed (in assembly language), a game based on the Intel 8085 microprocessor. EAGLE was used for building the schematic and board layout of the PCB, which was later self-soldered at CEPD, NSIT. Link to the demonstration video: https://www.youtube.com/watch?v=iUQp60EaMDg
## Project Overview
Kill-the-Virus is a lucid game-based project employing Intel 8085 microprocessor. It consists of a 6x6 LED matrix, with each lit-up LED approaching the player representing a 'virus' which is to be 'killed' by pressing the button corresponding to its column. There are two difficulty levels, which switch after a certain score is obtained. The number of kills make up the score, while missing even once causes the game to end. Points availed by the player will be displayed on a 16x2 LCD. IC 8255 will be used for input/ output interfacing. The choice to make a game for the project was made so as to extensively study the architecture and learn how to program the microprocessor. This will enable understanding the 8085 microprocessor in an exciting way, though detailed.

## Schematic Diagram

<img src="https://user-images.githubusercontent.com/32619706/149880580-b8c24fd7-1753-4189-b1a7-b57ae3998e97.png">

* The power supply is provided to the circuit using the mini-USB port.
* START and RESET button circuits are connected to the microprocessor.
* Five latches are used to latch all the LEDs present in the matrix.
* Except RST 7.5, all interrupts are grounded, as the RST 7.5 interrupt is employed for the project.
* Pins of port A of 8255 IC are interfaced with the LCD, which is to be used for displaying the score and the status of the game.
* Six pins of port B of 8255 IC are interfaced with the six-push button circuit. The outputs of all push buttons are passed through AND gate whose output either enables the interrupt RST 7.5 or not.
* The pins of Port C of the 8255 IC are used to drive the random number generator designed using the mod-8 counter. The random generator helps in switching on random LEDs in the LED matrix.
* Memory interfacing of EEPROM and RAM is done with the 8085 microprocessor and a decoder is used for relevant switching between both the memory devices.
* Capacitors are placed at the Vcc pin of every IC used so as to reduce noise and implement the debouncing technique.
* 4Mhz crystal oscillator is used to provide a clock frequency of 2MHz. A 22pF capacitor is used to provide proper impedance matching between the 8085 and the crystal as the crystal does not load immediately.
* The 8255 PPI is being used in Mode 0, i.e. no handshaking is required.
* The board is supplied by an external +5V power source with the help of a mini-USB port. A power LED incorporated alongside indicates that the circuit is receiving power.

## Board Layout

<img src="https://user-images.githubusercontent.com/32619706/149880735-116e7f3a-a007-4481-962a-9b6a5f211f31.png">

For hardware testing of the circuit board, the steps followed were as follows:

1. To check for inputs, a simple assembly language program was burnt in the EEPROM on the SID pin, expecting to result in the same as an output on the SOD line:


    `RIM` \
	`ANI 80H` \
    `ORI 40H` \
    `SIM`

	The output on the SOD pin was indicated using a red LED. The working of this program ensured the smooth functioning of the 8085 and the EEPROM.

2. The output ports were checked individually to verify the decoding logic.
3. Multiplexing was carried out for the LED matrix in the interrupt service routine using the RST 7.5 pin.
4. Input port was checked in the main program, along with the LED matrix being refreshed by the interrupt service routine running in the background.
5. Each IC was individually tested on the IC tester in the microprocessor lab.
6. Each port of 8255 PPI was tested.


## Gerber

<img src="https://user-images.githubusercontent.com/32619706/149880834-3e6f9052-f5f6-4145-bf30-d3f576dda6ab.png">

Tools:
* Soldering station and wire
* Tweezers, cutters, files
* Multi-meter

Software:
* EAGLE CAD
* Oshon Soft 8085 Simulator IDE
* EEPROM Programmer  
