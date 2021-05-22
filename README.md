# VARS_AutoSystem
Wireless home appliance control using 8051 [GSM + Bluetooth]. Built and tested using Keil uVision and Proteus 

#### [Video of operation](https://drive.google.com/file/d/1lxrP9cyHPhfxUEqP0h9ee0CDyieyZUmf/view?usp=sharing)
#### [HC-05 STATE operation](https://drive.google.com/file/d/1cMt5H4pJRYg0uKJ7UUtjo8AbJcdI7P5d/view?usp=sharing)

## Working explanation
- HC-05 TX and GSM module’s TX are multiplexed using a 4:1 MUX, where the select pin is connected to STATE pin of HC-05.
- The STATE pin goes HIGH when a Bluetooth device is connected. Hence the Bluetooth control is given higher priority over GSM control. [Tested using HARDWARE]
- The STATE pin is also an input to the 8051 to run subroutines according to the communication used.

### Bluetooth control
- In HC-05 Bluetooth mode, a Serial communication app in the smartphone has pre-programmed STRINGS according to conventions.
- When a button is pressed, the corresponding string is transmitted to HC-05 and therefore, it reaches the 8051 at a baud rate of 9600.
- The string is processed and corresponding appliance is switched ON/OFF using relays

### SMS control
- User sends a message asking the system to switch ON/OFF an appliance.
- The GSM module receives the message. It sends a message to the 8051 with the message location.
- The message location is extracted and AT commands are sent to the GSM module from the 8051 asking for the data SMS.
- The GSM module sends the message packet, with metadata like phone number, name, date and time.
- The 8051 parses and extracts the useful and required data.
- 8051 switches ON/OFF the appliance using relays accordingly.

### Final circuit
![circuit](https://user-images.githubusercontent.com/63254914/119237264-928b0580-bb59-11eb-8a1d-9d71e6203531.png)

### Test circuit
![test_circuit](https://user-images.githubusercontent.com/63254914/119237751-10501080-bb5c-11eb-92f1-058754c14bb2.png)



