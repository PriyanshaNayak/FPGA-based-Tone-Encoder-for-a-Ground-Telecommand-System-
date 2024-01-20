## FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-
A 3 tones, 2 commands FPGA-type tone encoder used in a telecommand system is a digital circuit implemented on an FPGA (Field-Programmable Gate Array) that is responsible for encoding two specific commands into three distinct audio tones. It converts the input commands into tone sequences that can be transmitted and decoded by the GTC.

# Ground Telecommand System 
Ground Tele-Command system has a significant role in the dynamic testing of flight vehicles especially missiles. It is a range safety tool for every missile testing range in the world. When the flight vehicle under test, deviates from its desired trajectory and crosses the safety zone then the TC system is used to terminate the vehicle to safeguard human lives and property. 
Here are some key reasons for the need for a ground TC system:
●	Remote Operations

●	Real-time Responsiveness

●	Efficiency and Cost-Effectiveness

●	Scalability and Flexibility

●	Training and Simulation

In the dynamic testing of flight vehicles, a ground telecommand system plays a crucial role in controlling and monitoring various aspects of the testing process. It serves as a communication link between the ground-based operators and the flight vehicle, allowing for real-time command and control during dynamic testing scenarios. 
# A.	Ground Control Station (GCS):
It includes computer systems, displays, communication interfaces, and specialized software for telecommand operations.

# B.	Communication Links:
Based on various technologies such as radio frequency (RF), satellite communication, or optical communication between the GCS and flight vehicles. 
Apart from these, there are various other components like the Telecommand Encoder, Telemetry Receiver, Telecommand Receiver, and Command Decoder/Processor. 
The overall configuration of the GTC is shown below : 
![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/c14ac471-7e70-41b0-b8c9-65d3338a3f58)
(Block Diagram of Ground Telecommand System)

From the figure it is clear that the system is a redundant hot-swappable system, each chain consists of a Digital Encoder, Modulator, Power Amplifier, and antennae with Command Console & Switch-Over Units in common between the two chains. Command Console insists the command to be transmitted and depending upon the command received the Digital Encoder generates a binary FSK modulated signal which is then fed to the Modulator for FM modulation. This signal is then power amplified and transmitted through omnidirectional or directional antennae depending upon the requirement. 

TC system generates four types of commands and transmits these commands on demand through a UHF link.
•	 SAFE command is transmitted normally which ensures the link between the ground TC system and missile onboard receiver. 
•	When termination is required then a sequence of commands like ARM, TT, and DESTRUCT are transmitted. These commands are received and decoded by the on-board receiver decoder and passed to the destruction system. ARM command allows activation of TT, TT command is used to cut off the thrust of liquid propellant and DEST command enables destruction system for termination. TT command is not required in case there is no liquid propellant. Full redundancy is incorporated on the ground as well as on the flight vehicle to cater to reliable operation under the worst conditions.

The Ground TC system is a dual-chain transmitting system with an Automatic change-over unit. Each transmitter chains consist of a command encoder interfaced with a Remote Command Panel (RCP), an FM modulator, and a High-power UHF amplifier. The function of the cache unit has been described below: 

1.	RSO PANEL: It is used for issuing required commands by the competent authority. This unit is interfaced in parallel with both the Command Encoders through copper cable or via an RS-232 communication interface.
2.	COMMAND ENCODER: These units are the baseband units. They are again of several types. Currently, there are two types of Encoder systems. (a) The Tone-based Encoder (IRIG-313). (b) Digital Encoder System. Tone Encoders are used from the beginning of the missile program. These Encoders generate different mixed IRIG (Inter-Range Instrumentation Group) tone outputs as decided when configuring the system for the direct commands. However, nowadays most missiles use a Digital Telecommand System with a Command Encoder. 
3.	FM MODULATOR: This unit is used for Frequency Modulation of the baseband signals from the Encoder system at the desired carrier frequency in the UHF band.
4.	POWER AMPLIFIER: The High-Power Amplifier is solid-state, reliable, and cool running, allowing max continuous 1- kW output power at ambient temperatures from 10° C to 40° C. The System is MIL-STD-9858A qualified and designed to military standards for high MTBF.
5.	ANTENNA: Used to radiate the modulated command signal in the air. Usually, Omnidirectional antennas with RH circular polarization are used so that in the worst case, even if the missile deviates much beyond its expected trajectory, the missile must be able to receive commands. 

6.	AUTO CHANGE OVER UNIT: This unit carries out the function of the centralized monitoring and control of the entire system. It continuously monitors the health of both the Transmitter chains and the antennas Forward power level, Reflected power level, VSWR fault, over temperature fault, status of all the power amplifier modules of the transmitter, etc. In case any of the transmitter chains is found to be faulty, it changes over to the backup chain. Similarly, if any of the antennas is found to be faulty, it changes over to the secondary antenna.
7.	DUMMY LOAD OR TERMINATOR: The output of the transmitter can be fed to a Dummy load instead of an antenna if required for some tests & measurements. Also, when any one of the transmitters is selected for transmission through any one of the two antennas the other transmitter (even if powered off) is automatically terminated to dummy load for safety. Again, in case both the antennas fail, then both the transmitters are terminated to dummy load.

# Components of Telecommand System in ITR :

<br> •	Command Centre: The command center serves as the control hub of the telecommand system. It consists of workstations, consoles, and communication equipment where operators or commanders issue commands and monitor the telecommand operations. The command center interfaces with various subsystems to send and receive command signals. <br>
<br> •	Command Encoder: The command encoder is responsible for encoding high-level commands or instructions into a suitable format for transmission. It takes the commands from the command center and converts them into specific signals, tones, or digital codes that can be transmitted over the communication channel. <br>
<br> •	Transmitter: The transmitter is the component that transmits the encoded command signals over the communication channel. It may utilize various communication technologies such as radio frequency (RF) transmission, satellite communication, or other wireless or wired communication mediums. <br>           
<br> •	Receiver: The receiver is responsible for receiving the transmitted command signals. It may include antennas, receivers, and demodulators to capture and extract the command signals from the communication channel. <br>
<br> •	Decoder: The decoder processes the received command signals and converts them back into meaningful commands or instructions. It interprets the encoded signals and provides the appropriate outputs for further action or execution. <br>
<br> •	Data Processing and Control Units: These units handle data processing, command validation, and coordination of telecommand operations. They may include microcontrollers, digital signal processors (DSPs), or specialized processing units to execute command logic, perform error checking, and manage overall system operations. <br>
<br> •	Telemetry and Communication Subsystems: These subsystems enable bidirectional communication between the telecommand system, and the platforms or devices being controlled. They allow for the transmission of telemetry data, status updates, and acknowledgment signals between the command center and the remote devices. <br>
<br> •	Power and Signal Conditioning Units: These units provide the necessary power supply and conditioning for the telecommand system components. They may include power management systems, voltage regulators, and signal conditioning circuits to ensure proper operation of the system. <br>

## Architecture of FPGA :

The architecture of an FPGA consists of several key components, including Configurable Logic Blocks (CLBs), interconnects, I/O pads, and a switching matrix. Here is a brief explanation of each component:
# 1. Configurable Logic Blocks (CLBs):
They consist of a collection of Look-Up Tables (LUTs), registers, multiplexers, and other logic elements. LUTs are programmable lookup tables that allow users to define the desired logic function within the CLB. The outputs of the LUTs can be routed to various destinations within the FPGA.

# 2. Interconnects:
Interconnects form the network of programmable connections within an FPGA, allowing the flow of signals between different components. They consist of a series of routing channels that run horizontally and vertically across the FPGA fabric. Interconnects provide the necessary paths for connecting the inputs and outputs of CLBs, as well as other components such as memory blocks and specialized functional units.

# 3. I/O Pads:
These pads act as the connection points for input and output signals, allowing communication between the FPGA and other devices. I/O pads typically support a variety of electrical standards, such as LVCMOS, LVDS, and differential signaling. They also provide features like voltage level translation, impedance matching, and protection circuitry.

# 4. Switching Matrix:
The switching matrix is responsible for establishing the connections between the input and output signals within an FPGA. It consists of a matrix of programmable switches that can be dynamically configured to establish the desired connections. The switching matrix enables the routing of signals from one CLB to another, allowing for the interconnection of various logic elements and the creation of complex digital circuits.

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/d88fee11-6397-4653-a964-28461a34c7cd)
(FPGA Architecture)

## DESIGN FLOW : 
<br> 1. Design Specification <br>
<br> 2. Design Entry <br>
<br> 3. Simulation and Verification <br>
<br> 4. Synthesis <br>
<br> 5. Place and Route <br>
<br> 6. Timing Analysis <br>
<br> 7. Bitstream Generation <br>
<br> 8. FPGA programming <br>
<br> 9. Post-Implementation Verification <br>
<br> 10. Iteration and Debugging <br>

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/25998758-26b2-44ad-bbd8-44b8566aeb39)
(FPGA design flow)

## Features of Xilinx Virtex-4 FPGA :
This user-programmable gate array offers a lot of features. These features include:

# Input/Output Blocks
I/O blocks have an interface between the internal configurable logic and package pins. Also, IOBs are specifically enhanced for source-synchronous devices. I/O blocks have different categories like:
<br> •	Per-bit deskew circuitry <br>
<br> •	Output block with a DDR or SDR register <br>
<br> •	Bidirectional block <br>
<br> •	Regional clocking resources and Dedicated I/O <br>
<br> •	In-built data deserializer/ serializer <br>
<br> •	Programmable differential or single-ended operation <br>
IOBs provide support for these single-ended standards:
<br> •	GTLP and GTL <br>
<br> •	LVCMOS <br>
<br> •	PCI-X <br>
<br> •	LVTTL <br>
<br> •	PCI (66 and 33 MHz) <br>
<br> •	SSTL 2.5V and 1.8V <br>
Also, IOBs can support differential signaling I/O standards like:
<br> •	ULVDS <br>
<br> •	LVDS <br>
<br> •	Differential SSTL 2.5V and 1.8V <br>
<br> •	BLVDS <br>
<br> •	Differential HSTL 1.8V and 1.5V <br>

## Block RAM
The block RAM can use large, embedded storage blocks. The resources here are 18Kb true dual-port RAM blocks.

# Boundary Scan
This supports a standard technique for configuring and assessing Virtex-4 devices. Also, the boundary scan complies with IEEE standards 1532 and 1149.1.

# Global clocking
This features a lasting solution for creating high-speed clock networks. There are about twenty DCM blozcks available. Also, there are about 32 global-clock MUX buffers in Virtex-4.

# Configurable Logic Blocks (CLBs)
A CLB features about four slices. Each slice comprises:
<br> •	Two storage elements <br>
<br> •	Large multiplexers <br>
<br> •	Two function generators <br>
<br> •	Arithmetic logic gates <br>
<br> •	Fast carry look-ahead chain Configuration <br>
Xilinx Virtex-4 FPGA’s configuration uses some modes to load the bitstream into internal configuration memory. These modes include:
<br> •	Slave Select MAP mode <br>
<br> •	Slave-serial mode <br>
<br> •	Boundary-Scan mode <br>
<br> •	Master Select MAP mode <br>
<br> •	Master-serial mode <br>

# Storage elements : 
Virtex-4 FPGA slice features storage elements. These elements can be configured as level-sensitive latches or D-type flip-flops. LUT output can drive the D input through the DY or DX multiplexer. The Clock Enable, Control Signals Clock, and the Set/Reset are common to these elements. Also, there is independent polarity in all control signals.
Any inverter on a control input becomes automatically absorbed. By default, the clock-enable signal is High. The clock enable goes to the active state if left unconnected. Furthermore, every slice features reset and set signals. The set/reset compels the storage element into the condition specified by SRLow or SRHigh.

# Arithmetic Logic :
This features an XOR gate that enables the implementation of a 2-bit full adder within a slice. Also, a dedicated GAND and FAND gate enhance the capability of multiplier implementation.

# Look-Up Table :
The two function generators in a slice feature four independent inputs each. The function generators can implement any arbitrarily defined four-input Boolean function.

# Carry Logic :
This offers fast arithmetic subtraction and addition. The CLB in Virtex-4 FPGA comprises two distinct carry chains. These chains have a height of two bits per slice. Virtex-4 device’s carry chain is running upward. You can also use the carry multiplexer and dedicated carry path to cascade function generators.

# Multiplexers :
The associated multiplexers and function generators in Virtex-4 FPGA can implement these:
<br>•	8:1 multiplexer in two slices<br>
<br>•	16:1 multiplexer in four slices<br>
<br>•	4:1 multiplexer in one slice<br>
<br>•	32:1 multiplexer in eight slices<br>
Wide input multiplexers are carefully used in one level of logic. Also, every slice features one MUFTX multiplexer and one MUXF5 multiplexer. MUXFX multiplexer uses the MUXF8, MUXF7, and MUXF6. MUXFX can allow combining LUT of about 16 LUTs. You can implement a 2:1 multiplexer for any LUT.

# Routing resources
Virtex 4 devices feature some components. These components utilize the same interconnect scheme. Also, the timing models improve the performance of high-performance designs.

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/7f569a02-e590-4bff-9885-58c1099537ee)
(Virtex-4 FPGA Block RAM)

# Block RAM in Virtex-4 

<br> Independent read and write port width selection <br>
<br> Byte-Wide write enable <br>
<br> Cascadable Block RAM <br>
<br> Optional Output Registers <br>
<br> Block RAM Port Signals <br>

# JTAG Chain:
In the Virtex-4 FPGA board, the JTAG (Joint Test Action Group) chain is a feature that allows for programming, debugging, and testing of the FPGA and other devices on the board.

# Boundary Scan Mode:
In Boundary Scan mode, the JTAG TAP (Test Access Port) controller sends instructions to the boundary-scan cells to perform specific operations. These instructions can include actions like reading and writing data to the pins, shifting test patterns into the device, capturing output responses, and observing the state of internal signals.

## Tone Encoders used in Telecommand System -

A 3 tones, 2 commands FPGA-type tone encoder used in a telecommand system is a digital circuit implemented on an FPGA (Field-Programmable Gate Array) that is responsible for encoding two specific commands into three distinct audio tones. It converts the input commands into tone sequences that can be transmitted and decoded by the receiving end of the telecommand system.

The tone encoder employs the FPGA's programmable logic resources to generate audio tones with specific frequencies, durations, and modulation characteristics. It utilizes a command-to-tone mapping scheme to associate each command with a unique combination or sequence of tones. This mapping ensures that each command is represented by a distinct set of tones, enabling accurate identification and interpretation on the receiving end.

The FPGA-based tone encoder incorporates additional features such as modulation techniques (e.g., amplitude modulation, frequency modulation) to enhance the transmission quality and improve the reliability of the encoded tones. It also manages the timing and synchronization of the generated tones to meet the telecommand system's timing requirements.

# Working: 
During missile testing, a 3-tone, 2-command FPGA-based tone encoder in a telecommand system serves the purpose of encoding two specific commands into three distinct audio tones. The tone encoder's operation in this context can be outlined as follows:
<br> 1.	Command Mapping: The tone encoder associates the two specific commands relevant to the missile testing (Command 1 and Command 2) with three unique audio tones (Tone 1, Tone 2, and Tone 3). The command mapping is designed to ensure that each command is represented by a unique combination of tones, enabling accurate identification and interpretation by the receiver or decoding system. <br>
<br> 2.	Tone Generation: The FPGA-based tone encoder generates the audio tones required for the missile testing scenario. The specific frequencies of Tone 1, Tone 2, and Tone 3 are carefully chosen to ensure distinguishability and compatibility with the communication channel used during the test. The duration of each tone is controlled to align with the system's timing requirements. <br>
<br> 3.	Command Encoding: The tone encoder encodes the two commands into specific tone sequences based on the predefined command mapping. For example, Command 1 may be encoded as Tone 1 followed by Tone 2, while Command 2 may be encoded as Tone 2 followed by Tone 3. The specific encoding scheme is determined based on the design and requirements of the telecommand system for missile testing. <br>
<br> 4.	Modulation: The generated tones may undergo modulation techniques, such as amplitude modulation (AM), frequency modulation (FM), or phase modulation (PM), to enhance transmission quality and improve the reliability of the encoded signals. Modulation can provide resistance against interference and noise, ensuring that the encoded commands remain intact during transmission. <br>
<br> 5.	Transmission: The modulated tone signals, representing the encoded commands, are transmitted over the communication channel. In the context of missile testing, this typically involves wireless transmission, such as radio frequency (RF) communication or dedicated telemetry systems. The transmission is carried out to ensure that the encoded commands reach the missile or testing equipment accurately. <br>
<br> 6.	Reception and Decoding: On the receiving end, the tone decoder or receiver captures the transmitted tones. The receiver is designed to decode the received tone sequences and identify the corresponding commands based on the predefined command mapping. By comparing the received tones with the expected tone combinations, the receiver accurately determines the intended commands. <br>
<br> 7.	Command Execution: Once the commands are decoded, the telecommand system initiates the execution of the desired actions or operations within the missile or associated testing equipment. The specific actions triggered by each command may vary depending on the objectives of the missile testing scenario, such as engine ignition, trajectory adjustment, or payload deployment. <br>

FPGA allows for flexible programming and configuration of the encoding logic, modulation schemes, timing control, and other essential features to meet the requirements of missile testing.

# Determination of Tones:
In a 3-tone, 2-command FPGA-based tone encoder used in a telecommand system, the determination of tones is based on the desired command-to-tone mapping. The specific tones used in the tone encoder are determined according to the following considerations:

<br> ●	Number of Tones: The system requires three distinct audio tones to accommodate the encoding of two commands. The selection of three tones provides enough combinations and variations to represent the different commands accurately. <br>
<br> ●	Frequency Selection: Each of the three tones used in the encoder will have a specific frequency associated with it. The frequencies should be chosen carefully to ensure distinguishability and compatibility with the communication channel or decoding system used in the telecommand system. The frequencies must be distinct enough so that they can be reliably detected and differentiated at the receiving end. <br>
<br> ●	Tone Duration: The duration of each tone is determined to meet the timing requirements of the telecommand system. The length of each tone should be sufficient for proper detection and decoding at the receiving end while considering any specific timing constraints or requirements of the system. <br>
<br> ●	Command-to-Tone Mapping: The mapping of the two commands (Command 1 and Command 2) to the three tones is predefined and designed based on the specific needs of the telecommand system. The mapping determines the tone sequences or combinations that represent each command. For example, Command 1 might be represented by Tone 1 followed by Tone 2, while Command 2 might be represented by Tone 2 followed by Tone 3. <br>

## Implementation of FPGA-Based Tone Encoder used in Telecommand Systems 

# Software Used: 
Xilinx ISE 13.2 (ISE Project Navigator and ISE iMPACT)

# Language Used: VHDL 
The Very High-Speed Integrated Circuit (VHSIC) Hardware Description Language (VHDL) is a language that describes the behavior of electronic circuits, most commonly digital circuits. VHDL can be used for designing hardware and for creating test entities to verify the behavior of that hardware. VHDL is used as a design entry format by a variety of EDA tools, including synthesis tools such as Quartus® Prime Integrated Synthesis, simulation tools, and formal verification tools.

# Board Used: 
Xilinx FPGA – Virtex-4 XC4VSX55-FF1148

# Block Diagram:

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/a770e5d0-3291-4ee1-9cbc-38a22daef941)

# Block Diagram Description:

# A. Inputs:

1. DIP Switch: This switch is used for giving commands. 
                          DIP = 1  =>  “SAFE” command
                          DIP = 0  =>  “DEST” command
                                
 DIP Switch Interface to FPGA
Dip Switches	FPGA Pin
net  "F_SW<1>"	 loc  =  "AB23";
net  "F_SW<2>"	 loc  =  "AB28";
net  "F_SW<3>"	 loc  =  "AC29";
net  "F_SW<4>"	 loc  =  "AC28";

2. System Clock: A system clock of frequency 40 MHz available in the Virtex-4 board is used.

3. Reset:  A reset will be generated if 3.3V drops below the 10% threshold value thereby preventing malfunction of the FPGA logic implementation due to the unwanted low voltage operations.
                                                         Clock-Reset Interface to FPGA
Control Bit	FPGA Pin	
F_CLK_200MHz	" F18";	200MHz
F_CLK_OPT	" H19";	40MHz 
F_RESET#	" AG31";	system Reset

# B. Functional Blocks:

    1. Direct Digital Synthesizer (DDS): A direct digital synthesizer (DDS) is a digital signal processing technique used to generate precise analog waveforms. It uses a phase accumulator, a waveform lookup table, and a digital-to-analog converter (DAC). The phase accumulator accumulates phase increments to determine the output frequency, the waveform table stores amplitude values for different phases, and the DAC converts the values into an analog signal. DDS offers high-frequency resolution, low phase noise, and flexibility in waveform generation, finding applications in communication systems, radar, test equipment, and more.

The output frequency of the DDS block is calculated as follows:

Given, Clock frequency, fclk = 10 MHz (output frequency from DCM block)
               
            FIW length (M) = 24 (Frequency Input Word is assigned for each tone frequency)

            Frequency Resolution, fmin = fclk / 2M

            Output frequency, fo = fmin• FIW

This way we get our tone frequency. 3 DDS blocks are used for 3 tones. We have used DDS where the input is 24 bits and the output is 12 bits.

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/737837a4-0f80-472e-8d42-23a0ab17f378)
(DDS Block Summary)

2. Digital Clock Multiplier (DCM): A Digital Clock Manager (DCM) is a digital circuit used to control and manipulate clock signals in digital systems. It adjusts timing characteristics such as frequency, phase, and duty cycle. DCMs are programmable and enable the synchronization of components within a system. They are widely used in applications requiring precise timing control, such as communication systems and data acquisition.

Here, we have taken 40 MHz from the system clock and divided it by 4 to make 10 MHz. This frequency is fed to DDS blocks for the synthesis of required tones.

3. Adder: 2 adder blocks of 12-bit inputs have been connected to the DDS blocks as shown in the block diagram.

# C. Output Blocks:
12-bit DAC: The sum of the 3 tone frequencies is passed through a 12-bit DAC which gives the output.
  
## Implementation Procedure:

<br> 1.	Design Entry - The design is created using a hardware description language (HDL) such as VHDL or Verilog, here we have used VHDL. The design entry can be done using a text editor or a graphical design entry tool (Xilinx ISE, here). <br>
<br> 2.	Behavioral Simulation - Change the view from Implementation to Simulation by clicking on the radio button beside the simulation. In the Design Menu, we choose Behavioural Simulation. The test bench for this design was set as a top level. Click on the test bench file and it will automatically show the simulator options in the processes window. Double-click on the Simulate Behavioural Model to launch the ISIm simulator. <br>
<br> 3.	Synthesis - A subset of the instructions can be used to describe a logic circuit that can be physically built from the instructions. The process of converting the code to a circuit implementation is called 'Synthesis' and the code is called Synthesizable code. <br>
<br> 4.	By clicking on the top-level file, it will show synthesis and implementation options in the processes window. Click Check Syntax under the synthesis option to check if VHDL sources are properly coded. After the syntax check is done, double-click on the synthesis option to synthesize your design. A green tick will appear showing that the synthesis is completed. The report from synthesis becomes available at the bottom of the window. <br>
<br> 5.	We can view the RTL Schematic (generates a schematic view of RTL netlist), Technology Schematic (generates a schematic view of Technology netlist), and generate a post-synthesis simulation model by clicking on the option available under synthesis. <br>
<br> 6.	Implement design - This step involves 3 processes namely, <br>
<br> 7.	Translation: converts and optimizes the HDL code into a set of components that the synthesis tool can recognize. <br>
<br> 8.	Mapping: translates the components from the compile stage into the target technology’s primitive components. <br>
<br> 9.	Placing and Routing means the placement and position of the interconnecting wires and CLBs of FPGA for successful synthesis. <br>
<br> 10.	Double-click on the implementation menu to start the implementation. It will automatically translate, map, place, and route one after the other. We can see the green tick with each option indicating that they are completed. <br>
<br> 11.	Bit Stream Generation -  Choose Generate Programming File, right-click and a pop-up menu should appear. Choose Run to start the bit generation process. <br>
<br> 12.	We can then open the ISE iMPACT for Boundary Scan, which means the FPGA board will be connected to the system via the JTAG cable. Click on Initialise Chain, which checks if the connection is made properly or not. (Software to Hardware) <br>
<br> 13.	Assign a new Configuration file (the newly generated bit file) on the Virtex-4 FPGA board. <br>
<br> 14.	Right-click on it, then select program it. It shows “Program Succeeded” that is, the VHDL code has been correctly dumped onto the FPGA board. <br> 
<br> 15.	The board is connected to the Mixed Signal Oscilloscope via a BNC cable, and after clicking on Run, we can see the output of the Adder2 on the oscilloscope. <br>
<br> 16.	The sinusoidal signal is the resultant of 3 DDS signals, and it has a breaking waveform. Smoothing filters and modulation techniques can be used to get the encoded output. <br>

## Implementation Results 
# RTL Schematic Diagram:

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/c1bb5d01-a718-470b-b88d-b7b14135c8a8)

# Boundary Scan:

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/c1a9b3da-14cd-4fb1-b6e7-353d725f35fb)

# Simulation Results:

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/a2810a18-bebd-4020-9658-f1b6d0ec1533)
(CRO Waveform) 

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/c83ef696-62c8-4b62-9b53-87fd72a853e6)
(Spectrum of Mixed Tones)

# Design Summary : 

![image](https://github.com/PriyanshaNayak/FPGA-based-Tone-Encoder-for-a-Ground-Telecommand-System-/assets/87187181/2223f691-dc4d-42b8-a0e7-a54d5a389acb)


















