# CoffeeBot
A coffee brewing robot using a Universal Robot arm.

<img width="515" height="853" alt="image" src="https://github.com/user-attachments/assets/5e253199-0a83-4099-b836-4160cca4c1d0" />

This project uses a Universal Robot to brew coffee using a V60. The brewing technique is inspired by the 1 cup V60 brewing recipe by James Hoffmann (https://www.youtube.com/watch?v=1oB1oDrDkHM).

This GitHub repository explains in 3 subfolders how the (1) process is set up and working, (2) MQTT service is set up and connected and (3) hardware is design. All relevant files including the CAD files, the code for the robot and the process are provided. Additionally, a video and pictures of the process and the parts are provided. 

<img width="1429" height="767" alt="image" src="https://github.com/user-attachments/assets/4701624a-e0ed-4ba9-b168-f03946551f35" />



## How to use the CoffeeBot when everything is set up:

### Preparations (pictures below):
1) Grind 15g of coffee beans
	- Our final grinding size for a 250ml V60 brew: 16 clicks from 0 with the chestnut c3 grinder
 	- Overview grinding sizes chestnut c3: https://honestcoffeeguide.com/timemore-c3-grind-settings/ (Individual Finetuning recommended)
3) Fill the gooseneck kettel to the max marking
4) Pre-wet the filter and the V60
5) Put the coffee into the V60
6) Ensure the kettle is plugged into the smart plug and the smart plug is turned on and connected to the MQTT server (see MQTT folder)
8) Ensure the robot server is running and the robot is in romote control mode

### Brew coffee:
1) Start the process engine
2) Turn on the kettle

### What the robot does:
1) Kettle heats up and is detected by the MQTT service
2) MQTT service sends a signal to the process engine once the kettle reaches the desired temperature
3) Engine starts the process automatically
4) Robot picks up the kettle
5) Robot pours water over the prepared V60
6) Brewing is executed in 5 pouring rounds
  •	Each pouring round uses approximately 50 g of water
	•	Total of 250 g of water is poured into the cup

(Attached video demonstrates the complete pouring process
https://github.com/user-attachments/assets/f163f936-66f3-4e5c-83a3-607d5750748c)

## Bill of Materials (BOM)

### Coffee Brewing Components
- **V60 Dripper (Plastic, size 01)**  
  Hario V60 Plastic Dripper  
  https://www.amazon.de/dp/B001HC9GIC
- **V60 Paper Filters (size 01)**  
  Hario VCF-01  
  https://www.amazon.de/dp/B001U7CVEA
- **Gooseneck Kettle (temperature-controlled)**  
  https://www.amazon.de/dp/B0CPJ447NZ
- **Manual Coffee Grinder**  
  Timemore Chestnut C3 Pro  
  https://www.coffeefriend.de/p/manuelle-kaffeemuehle-timemore-chestnut-c3-pro-black/
- **Coffee Beans**  
  Lavazza Qualità Oro  
  https://www.coffeefriend.de/p/kaffeebohnen-lavazza-qualita-oro-1-kg/
- **Scale**  
  Any fine-resolution coffee scale (≥ 0.1 g accuracy recommended)
- **Cup**  
  Standard coffee cup

### Automation & Control
- **Smart Socket**  
  NOUS smart socket with power measurement  
  https://www.amazon.de/dp/B0DDJVJJPM
- **MQTT Server**  
  Required for kettle state detection and process control

### Robotics & Fixtures
- **Universal Robot**  
  Used for kettle handling and pouring
- **V60 Stand**  
  Custom 3D-printed part (see subfolder)
- **Gooseneck Kettle Holder**  
  Custom 3D-printed part (see subfolder)
- **Gooseneck Kettle Handle Adapter (for robot gripper)**  
  Custom 3D-printed part (see subfolder)



## Further Automation Opportunities:
### Automation of the coffee grinding process
  - Integration of the Chestnut C3 grinder into the robotic workflow
  - Removal of the grinder’s top lid to allow direct robotic access
  - Adaptation of a nut tool to interface with the grinder’s grinding mechanism
  - Removal of the screw-on coffee collection container at the bottom of the grinder
  - Mounting of the remaining grinder body onto a custom 3D-printed holder
  - Use of a 3D-printed adapter to enable the robot to actuate the grinder
  - Filling of coffee beans into the adapted grinder using the robot
  - Grinding of beans into a small collection pot using the robot
  - Handling of the pot and transfer of ground coffee into the V60 using the robot
    
### Automation of the filter cleaning using a reusable metal filter
  - Replacement of paper filters to enable robotic handling and reuse
  - Robotic removal of the metal filter after completion of the brewing process
  - Placement of the metal filter onto the existing glass cleaning station in the lab
  - Positioning of the V60 on top of the metal filter at the cleaning station
  - Robotic actuation to press down the filter and V60 to initiate cleaning
  - Optionally: design and 3D printing of a protective cap for the open end of the metal filter to prevent water splashing and soaking during the automated cleaning process

### Integration of a scale into the CoffeeBot setup  
  -  Continuous measurement of brewed coffee weight during pouring
  -  Use of weight-over-time data as feedback for grind size optimization
  -  Detection of fast water flow as an indicator of overly coarse grind size
  -  Detection of slow water flow as an indicator of overly fine grind size
  -  Closed-loop feedback to adapt grind size in subsequent brewing runs
  -  Automatic optimization of brewing parameters based on target flow behavior
  -  Reduction of sour taste caused by overly coarse grinding
  -  Reduction of bitter taste caused by overly fine grinding  
 
## Pictures of the set up:

   <img width="447" height="499" alt="image" src="https://github.com/user-attachments/assets/17beff41-ae47-45ae-bacf-c10728161ab9" />
   <img width="770" height="766" alt="image" src="https://github.com/user-attachments/assets/97e8f968-6c6b-4918-b030-29f60a02a14c" />
   <img width="444" height="777" alt="image" src="https://github.com/user-attachments/assets/83485e9b-dace-4cf4-a0a6-f7db8a6bafce" />
   <img width="802" height="505" alt="image" src="https://github.com/user-attachments/assets/61bfd1e8-221f-4d82-94df-8358eee6fbb6" />
   <img width="822" height="902" alt="image" src="https://github.com/user-attachments/assets/eca3dedf-21ab-4e0b-b598-f66255e87854" />
   





