# Ice_Machine_Praktikum23-24

# Context
This report describes the development of a robot to operate an ice-machine. 
The robotic arm was designed to pick up a glass and guide it to the ice-machine. 

# Description
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
The server did not receive new features, however, minor improvements have been made. The name of the port on which the server expects the ice machine was previously hard-coded. Plugging and unplugging the machine from the server could therefore result in the port being renamed and the Python server no longer having a connection to the ice machine. The port can now be statically located under the following symlink: `/dev/serial/by-id/usb-FTDI_FT232R_USB_UART_B001B4FM-if00--port0 `. This means that you no longer need to adapt the device name.
The Python code of the server is located on the lab computer under `/project/ice-machine/icemachine.py`.



# Box
To store the multicontroller and the switch well, I replaced last year's box with a larger and more functional box and 3D printed the new box. The box has a sliding lid. There is a small knob on the sliding lid which makes it easier to open the box. The box has two holes. 
One hole for the cables and one for the USB stick connection. The holes are extended from the inside with a holder from the inside so that the inserted cables do not kink. 
See picture:
Below you can see the pictures of how the box looks and the comparison with the old box:

![IMG_7009 3](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/5a185c6c-f5ab-4c80-9261-2b62427c8af0)
![IMG_7005](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/04b43e11-70f3-4dd8-b2e1-00489c9bedeb)
![IMG_7006](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/6bb2cc35-0f18-4bf8-830b-7fd05730082f)
![IMG_7004](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/295ba3af-56b7-473c-9280-91b4521666a9)

For The 3D print I used the Tinkcard programme.
Link to the WebPage: [https://www.tinkercad.com]
Tinkercad is a free solution for realising 3D projects and is well suited for beginners. Several people can work on a project at the same time.
Below you will find pictures of the box design in the programme:
<img width="634" alt="Bildschirmfoto 2024-04-13 um 12 34 52" src="https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/1cafd8a7-52c4-430c-b9a9-aa2d23e288b9">
<img width="469" alt="Bildschirmfoto 2024-04-13 um 12 35 25" src="https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/3edbc452-8dfe-4640-86d5-79574713159e">
<img width="602" alt="Bildschirmfoto 2024-04-13 um 23 30 13" src="https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/021bb4e5-4c05-473f-b2ac-098df990aa75">
<img width="408" alt="Bildschirmfoto 2024-04-13 um 23 29 48" src="https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/7b896d0b-dee8-43f8-97f9-57f3bca33338">
<img width="714" alt="Bildschirmfoto 2024-04-13 um 23 30 42" src="https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/d6d9f0bd-ad1c-44f2-a256-e658d1ace917">
<img width="714" alt="Bildschirmfoto 2024-04-13 um 23 30 52" src="https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/65be7d99-9076-41a6-ad32-ca20fd48909f">

Here is the file for the SL






