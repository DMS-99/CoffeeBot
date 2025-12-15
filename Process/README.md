Process (a): <img width="543" height="557" alt="image" src="https://github.com/user-attachments/assets/c9d435fc-f870-4f1a-b649-03cd727eb03d" />

Process (b): <img width="544" height="517" alt="image" src="https://github.com/user-attachments/assets/c28a46f8-d2ae-4b9b-ae94-39ce063ce997" />

The image above shows the process model. It can be accessed via the the CPEE process engine under /Teaching/Prak/TUM-Prak-25-WS/SchmittDavid. 

Process Description:

The brewing process is initiated with a parallel control structure. In one branch, the robot continuously monitors the MQTT service, listening for incoming sensor data. Specifically, the robot evaluates the RSS sensor value to detect whether the kettle is actively heating.

Once the MQTT service reports an RSS sensor value greater than 5, indicating that the kettle has started heating, the second branch of the parallel process is activated. In this branch, the robot arm begins moving toward the kettle in preparation for pickup.

When the RSS sensor value drops below 5—corresponding to the kettle finishing the heating process—the parallel section is terminated. The robot then proceeds to pick up the heated kettle and moves it to the predefined pouring start position.

From this position, the robot executes the pouring routine. Depending on the selected control script, this is achieved either by (a) transmitting the required number of pouring loop iterations to the robot before execution, or (b) directly executing the predefined pouring process.

After the pouring sequence is completed, the robot returns the kettle to its initial position and finally moves back to its home position, concluding the process.

