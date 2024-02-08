## Setting Up can-utils
<p>sudo apt-get install libsdl2-dev libsdl2-image-dev can-utils</pbr>
  installs packages required to use can-utils</p>

## Loading Necessary Linux Kernels
<p>sudo modprobe can<br>
  loads CAN kernel module on linux which allows us to work with CAN devices on the system<br></p>
sudo modprobe vcan<br>
  loads Virtual CAN kernel module on linux system which sets up a virtual CAN network as I do not have access to a physicall CAN connection</p>

## Setting Up And Activating Virtual Can Devices
<p>sudo ip link add dev vcan0 type vcan<br>
    sets up a virtual CAN network with virtual device named vcan0<br></p>
  <P>sudo ip link set up vcan0<br>
    activates the device vcan0<br></P>

## Setting up ICSim
<p>Loaded up ICSim and controls in seperate terminal tabs.<br>
  
Set up cansniffer at vcan0, colour coded changing data by using -c argument (cansniffer -c vcan0)<br>

entering shift+3 multiple times into cansniffer filters out most of the changing data, leaving the output much cleaner and able to focus on the changes corresponding to user inputs<br>

the rapidly changing data seen across almost all arbitration ID's before filtering is due to the "controls" program simulating an engine idle<br></p>

## Cracking the flag
<p>Found out arbitration id to increase speed is 244, by running (cansniffer -c vcan0)<br>
  using cansend, sent a data packet with arbid 244 high enough to break past the speed limit imposed<br></p>
<P>data is in hexadecimal format. Therefore crafting an input with a lot of F's towards the end will max out the speedometer<br>
cansend vcan0 244#000000ffff maxes out the speedometer and reveals the flag<br></p>

flag is : wired{y0u_c4n}

