# Ice_Machine_Praktikum23-24

# Context
This report describes the development of a robot to operate an ice cream machine. 
The robotic arm was designed to pick up a glass and guide it to the ice machine. 

# Descriptin 
The robotic arm positions the glass correctly on the ice machine so that the ice can fall directly into the glass. 
While the ice falls into the glass, the robot arm holds the glass. It then returns the glass and returns to the starting position itself. 
A total of 8 sub-movements have been defined, which enable an overall movement.


1. From Home Postion to Glas
2. Pick up the glas
3. Hover to Ice Machine 
4. Put the glas on the Ice Machine
5. Wait until glas is filled with ice
6. Move Glas away from the Ice Machine
7. Put glas down to start postion
8. Arm goes back to home Position

[can Video]


# Ice Machine 
An ice machine from the manufacturer Klarstein was used for the project. 
Inside there is a water tank, a cup for making the ice cubes and a spiral that pushes the finished ice cubes into the dispenser.
Nachdem die Eis Maschine eingeschlaten wurde ernscheint auf dem Display das on off Zeichen. Hierbei muss die der On/Off Knopf betätigt werden. Um doe Maschine einzuschalten. 

Folgende Knöpfe sind vorhanden:

On/Off: Ein- bzw. Ausschalten der Maschine
Timer: Einstellen einer Zeit, Wert auf dem Display steigt mit jedem Drücken um 0,5h
Select: Auswahl, ob große oder kleine Eiswürfel produziert werden sollen
Ice: Wechselt den Zustand, ob Eis ausgegeben wird oder nicht
Water: Wechselt den Zustand, ob Wasser ausgegeben wird oder nicht

# Schaltung
The circuit was already assembled last year. There is a multicontroller and an FT232 chip. 
This allows it to be connected to a computer via a USB connection. On the other side, several pins are available for connecting electronic components.
Of the pins described above, VCC and RTS were used to build the circuit. For a more detailed documentation see [reference to repo by Denis]
The following pictures show how the pins were connected so that they can be reconnected if something should come loose.


# Server
The server was also not further developed compared to the previous year. However, improvements have been made. The connection to the server was hard-coded, which is why the port changed on one and the device name had to be reselected. This meant that the server could no longer establish a connection to the ice cream machine. 
The Python for the server can be found via the terminal call ssh lab and in the path: /project/ice-machine/icemachine.py
The device name is: '/dev/serial/by-id/usb-FTDI_FT232R_USB_UART_B001B4FM-if00--port0'
This means that you no longer need to adapt the device name.



# Box
The box containing the multicontroller and the circuit was reprinted. I used the Tinkcard programme for this.
Link: https://www.tinkercad.com
Tinkercad is a free solution for realising 3D projects and is well suited for beginners. Several people can work on a project at the same time.

Hier für habe ich einen etwas größer Box als die vom Vorjahr gebaut. Die Maßen sind:
Der Deckel hat de Maße: 

Siehe Bild:

Die Box hat einen Schiebe deckel. Auf dem Schiebe Deckel ist ein kleiner noppen Dies erleichert das öffnen der Box. DIe box hat zwei löcher. 
Ein Loch für die Kabel und eins für den USB Stick anschluss. Die Löcher sind von innen erweiter mit einer halterung von innen, sodass die eingeführten Kabel nicht um knicken. 
Siehe bild:







