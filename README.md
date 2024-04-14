# Ice_Machine_Praktikum23-24

# Structure
- Context
- CPEE for process control
- Ice Machine
- Circuit
- Server
- Box
- 3D Print

# Context
Our practical assignment focused on creating a cocktail mix using a robot. My task within this assignment involved ensuring the drinks remain chilled by filling the glass with ice cubes, facilitated by the robot's assistance. The robot precisely positions the glass beneath the ice cube dispenser, allowing the cubes to fall directly into it. Throughout this process, the robot securely holds the glass to prevent any spillage. Once the glass is filled, the robot places it back and returns to its initial position. This task is accomplished through the coordination of 8 distinct sub-movements, which collectively achieve the desired outcome. We utilized the CPEE environment for process control.

#### a. The 8 sub-movements
1. `Home Position to Glass`
2. `Retrieve the Glass`
3. `Hover Over the Ice Machine` 
4. `Place the Glass on the Ice Machine `
5. `Allow the Glass to Fill with Ice`
6. `Move the Glass Away from the Ice Machine` 
7. `Set the Glass Down to Its Starting Position`
8. `Return the Robot to Its Home Position`

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
The process engine initiates with the `Starttohover` process, linked to the `hometohover` endpoint. This process orchestrates the movement of the robot from its initial position to the designated start position, thus commencing the subsequent processes..
##### 2.GotoGlass
The `GoToGlas` process is linked with the `hovertoglas` endpoint. This configuration enables the robot to align itself with the height of the glass, facilitating the subsequent task of picking it up.
##### 3. GoToMachine
The process `GoToMachine` is linked with the endpoint `hovertomachine`. This process involves the robot positioning the glass at the same height as the ice cube machine.
##### 4. PutGlasDown
The process `PutGlasDown` is associated with the endpoint `putglasdown`. However, contrary to the expected procedure of placing the glass directly beneath the opening from which the ice cubes fall, the robot positions the glass in close proximity to the opening. This proximity ensures that the ice cubes fall directly into the glass, minimizing the risk of any cubes bouncing out from the sides.
![IMG_7734](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/489b9813-6422-4f03-b01e-9df140182007)
##### 5. Ice Machine
The `Ice Machine` process is linked with the endpoint `getIce`. During this process, ice cubes are dispensed from the ice machine. A server call with a waiting duration of 5 seconds is implemented here, allowing for the retrieval of the ice cubes. This waiting time can be customized within the endpoints through the URL parameters.
##### 6. GoAway
The process `GoAway` is connected with the endpoint `awayicemachine`. This step involves removing the glass, now filled with ice cubes, from the ice cube machine.
##### 7. DropGlas
The process `DropGlas` is connected with the endpoint `dropglas`. It involves returning the glass to its initial position before gently placing it down.
##### 8. BackToStart
The process `BackToStart` is linked with the endpoint `backtostart`. This final step involves the robot returning to its initial starting position.

# Ice Machine 
An ice machine from Klarstein was used for the project. This machine has a water tank, an ice cube mould and a spiral mechanism that transports the freshly made ice into the dispenser. When the ice machine is plugged into a socket, the on/off symbol appears on the display panel.
#### To activate the machine, simply press the on/off button. This action will result in the display appearing as follows:
![59B8C38F-99DA-40E5-9F92-4835F0F51B44](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/0776b5dc-eb08-4ba0-8141-29ae59371ba2)

# Circuit
The circuit was assembled last year, comprising a multicontroller and an FT232 chip. This configuration enables connection to a computer via a USB interface. On the opposite side, multiple pins are provided for connecting electronic components. Among these pins, VCC and RTS were utilized in constructing the circuit. For further detailed documentation, please refer to the [git repository from last year](https://gitlab.lrz.de/000000000149F516/tum-prac.git). 


The following images illustrate the pin connections, facilitating easy reconnection in case of any disconnection:
![70C0D7CB-EFC6-41F7-BC74-27A6205E7CF9 2](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/b6f06479-32a7-4d87-81cf-4d1e3be6be06)
![6253D19A-D63D-412D-A692-30F02F3C0D7B 2](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/d7f9c091-b195-404f-9c33-63bee672780a)
![3F5FF154-71EE-4A50-9B7D-52D13251CE9E 2](https://github.com/avvau/Ice_Machine_Praktikum23-24/assets/164665089/f091c205-4247-471e-9588-e9eb4465d806)


# Server
The server did not receive new features, however, minor improvements have been made. The name of the port on which the server expects the ice machine was previously hard-coded. Plugging and unplugging the machine from the server could therefore result in the port being renamed and the Python server no longer having a connection to the ice machine. The port can now be statically located under the following symlink: `/dev/serial/by-id/usb-FTDI_FT232R_USB_UART_B001B4FM-if00--port0 `. This means that you no longer need to adapt the device name.
The Python code of the server is located on the lab computer under `/project/ice-machine/icemachine.py`.



# Box
To accommodate the multicontroller and the FT232 chip, I replaced last year's box with a larger and more practical one that I 3D printed. This new box has a sliding lid for easy access. A small button on the sliding lid makes it easy to open. The case also has two openings: one for the cables and another for the USB port. Inside the box, these holes are extended by holders to prevent the inserted cables from being kinked or crushed.

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
Tinkercad is a free solution for realising 3D projects and is well suited for beginners. Several people can work on a project at the same time. The exported file for 3D printing can be found here in the repository under the folder name [3D print](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/899551233907259fdd71c0b20a0c31b6a81b5334/3D%20print) The files were separated into [Box](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/76ea0e92f8df307696dbfda43d05e6d6cca4ce1b/3D%20print/Box%20files) and [Deckel](https://github.com/avvau/Ice_Machine_Praktikum23-24/tree/899551233907259fdd71c0b20a0c31b6a81b5334/3D%20print/Deckel%20files)

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




