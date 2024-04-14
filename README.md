# Ice_Machine_Praktikum23-24

# Structure
- Context
- CPEE for process control
- Ice Machine
- Circuit
- Box
- 3D Print

# Context
The aim of our praktikum was to make a cocktail mix with the robot. My part of the cocktail mixing task is to fill the glass with ice cubes with the help of the robot so that the drinks stay cool.
To do this, the robot positions the glass on the ice cube machine so that the ice cubes fall directly into the glass. While the ice cubes fall into the glass, the robot continues to hold the glass. It then puts the glass back and returns to its starting position.
A total of 8 sub-movements have been defined, which enable an overall movement. The CPEE environment is used for process control.

#### a. The 8 sub-movements
1. `From home postion to glas`
2. `Pick up the glas`
3. `Hover to ice machine` 
4. `Bring the glas on the ice machine `
5. `Wait until glas is filled with ice`
6. `Move glas away from the ice machine` 
7. `Put glas down to start postion`
8. `Robot goes back to home position`

#### b. Video of robot gets ice cubes
[Video of robot gets ice cubes](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/0292e08a-dd6c-4daa-80a3-537b58f087ec)


# CPEE for process control
> CPEE is in the process hub folder [TUM-Prak-23-WS](https://cpee.org/flow/edit.html?monitor=https://cpee.org/flow/engine/36621/) or [`CPEE`](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/76ea0e92f8df307696dbfda43d05e6d6cca4ce1b/CPEE)
## Process Execution Engine Endpoints
![Endpoints](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/bdba5dd6-84ad-4598-aa1d-f44debefbe53)

## Process Execution Engine Architecture
![Process Architecture](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/7d231a92-ffd1-4e47-b2c4-10adc50b6182)

### How the endpoints are connected with the architecture
##### 1. Starttohover
The process engine starts with the `Starttohover` process. This process is connected with the `hometohover`endpoint. It moves the robot from its starting position to the start position to start the process.
##### 2.GotoGlass
The process `GoToGlas` is connected with the endpoint `hovertoglas`. This means that the robot positions itself at the height of the glass in order to pick it up.
##### 3. GoToMachine
The process `GoToMachine` is connected with the endpoint `hovertomachine`. In this process, the robot brings the glass to the height of the ice cube machine 
##### 4. PutGlasDown
The process `PutGlasDown` is connected with the endpoint `putglasdown`. But here, the glass is not put under the opening from which the ice cubes fall out, as one would assume from the description. Instead, the robot holds the glass so close to the opening so that the ice cubes can fall directly into the glass and do not jump out from the side.
![IMG_7734](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/489b9813-6422-4f03-b01e-9df140182007)
##### 5. Ice Machine
The process `Ice Machine` is connected with the endpoint `getIce`. In this process, ice cubes come out of the ice machine. The server call wait with a duration of 5 seconds is used here. This time can be adjusted in the endpoints via the URL. The server call wait with a duration of 5 seconds is used here. This time can be adjusted in the endpoints via the URL.
##### 6. GoAway
The process `GoAway` is connected with the endpoint `awayicemachine`. The filled glass with ice cubes is now removed from the ice cube machine.
##### 7. DropGlas
The process `DropGlas` is connected with the endpoint `dropglas`. The glass is returned to the starting position and then put down.
##### 8. BackToStart
The process `BackToStart` is connected with the endpoint `backtostart`. Finally, the robot returns to its starting position.


# Ice Machine 
An ice machine from the manufacturer Klarstein was used for the project. Inside there is a water tank, a cup for making the ice cubes and a spiral that pushes the finished ice into the dispenser. After the ice cube machine has been plugged into the socket, the on/off symbol appears on the display.
#### To switch the machine on, press the on/off button. So that the display looks like this:
![59B8C38F-99DA-40E5-9F92-4835F0F51B44](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/0776b5dc-eb08-4ba0-8141-29ae59371ba2)

# Circuit
The circuit was already assembled last year. There is a multicontroller and an FT232 chip. This allows it to be connected to a computer via a USB-C connection. On the other side, several pins are available for connecting electronic components. Of the pins described above, VCC and RTS were used to build the circuit. For a more detailed documentation see the [git repository from last year](https://gitlab.lrz.de/000000000149F516/tum-prac.git). 

The following pictures show how the pins were connected so that they can be reconnected if something should come loose.
![70C0D7CB-EFC6-41F7-BC74-27A6205E7CF9 2](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/b6f06479-32a7-4d87-81cf-4d1e3be6be06)
![6253D19A-D63D-412D-A692-30F02F3C0D7B 2](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/d7f9c091-b195-404f-9c33-63bee672780a)
![3F5FF154-71EE-4A50-9B7D-52D13251CE9E 2](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/f091c205-4247-471e-9588-e9eb4465d806)


# Server
The server did not receive new features, however, minor improvements have been made. The name of the port on which the server expects the ice machine was previously hard-coded. Plugging and unplugging the machine from the server could therefore result in the port being renamed and the Python server no longer having a connection to the ice machine. The port can now be statically located under the following symlink: `/dev/serial/by-id/usb-FTDI_FT232R_USB_UART_B001B4FM-if00--port0 `. This means that you no longer need to adapt the device name.
The Python code of the server is located on the lab computer under `/project/ice-machine/icemachine.py`.



# Box
To store the multicontroller and FT232-Chip, I replaced last year's box with a larger and more functional box and 3D printed the new box. The box has a sliding lid. There is a small knob on the sliding lid which makes it easier to open the box. The box has two holes. One hole for the cables and one for the USB connection. The holes are extended on the inside with a holder so that the inserted cables are not kinked.

### Pictures of the current box and comparison with the old box:

#### Current box
![IMG_7009 3](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/5a185c6c-f5ab-4c80-9261-2b62427c8af0)

#### Comparison with the old box
![IMG_7005](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/04b43e11-70f3-4dd8-b2e1-00489c9bedeb)

#### Front side
![IMG_7006](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/6bb2cc35-0f18-4bf8-830b-7fd05730082f)

#### Back side
![IMG_7004](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/295ba3af-56b7-473c-9280-91b4521666a9)

# 3D Print
For The 3D print I used the Tinkcard programme.
Link to the WebPage: [Tinkcard](https://www.tinkercad.com).
<br>
Tinkercad is a free solution for realising 3D projects and is well suited for beginners. Several people can work on a project at the same time. The exported file for 3D printing can be found here in the repository under the folder name [3D print](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/899551233907259fdd71c0b20a0c31b6a81b5334/3D%20print) The files were separated into [box](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/76ea0e92f8df307696dbfda43d05e6d6cca4ce1b/3D%20print/Box%20files) and [Deckel](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/899551233907259fdd71c0b20a0c31b6a81b5334/3D%20print/Deckel%20files)

### Tinkcard Design:
#### Dimensions of the box
> The dimensions are given in inches
![TEST](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/1cafd8a7-52c4-430c-b9a9-aa2d23e288b9)

#### Dimensions of the lid
> The dimensions are given in inches
![TEST](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/3edbc452-8dfe-4640-86d5-79574713159e)

#### Upper view
![TEST](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/021bb4e5-4c05-473f-b2ac-098df990aa75)
![TEST](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/7b896d0b-dee8-43f8-97f9-57f3bca33338)

#### Inner extension for the cable
![TEST](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/d6d9f0bd-ad1c-44f2-a256-e658d1ace917)

#### Inner extension for the USB-C stick
![TEST](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/65be7d99-9076-41a6-ad32-ca20fd48909f)




