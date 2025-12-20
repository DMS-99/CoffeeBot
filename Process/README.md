# Process (a): 

<img width="543" height="557" alt="image" src="https://github.com/user-attachments/assets/c9d435fc-f870-4f1a-b649-03cd727eb03d" />

# Process (b): 

<img width="544" height="517" alt="image" src="https://github.com/user-attachments/assets/c28a46f8-d2ae-4b9b-ae94-39ce063ce997" />

The images above show the process models. They can be accessed via the the CPEE process engine under /Teaching/Prak/TUM-Prak-25-WS/SchmittDavid. 

# Process Description:

The brewing process is initiated with a parallel control structure. In one branch, the robot continuously monitors the MQTT service, listening for incoming sensor data. Specifically, the robot evaluates the RSS sensor value to detect whether the kettle is actively heating. 

Once the MQTT service reports an RSS sensor value greater than 5, indicating that the kettle has started heating, the second branch of the parallel process is activated. In this branch, the robot arm begins moving toward the kettle in preparation for pickup.

When the RSS sensor value drops below 5 — corresponding to the kettle finishing the heating process — the parallel section is terminated. The robot then proceeds to pick up the heated kettle and moves it to the predefined pouring start position. 

From this position, the robot executes the pouring routine. Depending on the selected control script, this is achieved either by (a) transmitting the required number of pouring loop iterations to the robot before execution, or (b) directly executing the predefined pouring process.

After the pouring sequence is completed, the robot returns the kettle to its initial position and finally moves back to its home position, concluding the process.



The robot files called from the process enginee are provided below. One file that needs a bit of elaboration is the pourcoffee.urp file which executes the pouring process.

The file pourcoffee.urp implements the coffee pouring routine executed by the robot using the kettle. A central control variable in this program is num_loop, which defines the number of pouring rounds. This variable can either be assigned a fixed value — set to 5 in the current configuration to represent five pouring rounds — or dynamically assigned to in0. In the latter case, the number of pouring rounds is retrieved via Process (a) from the process engine and subsequently used to execute the pouring routine.

The pouring motion is parameterized around a variable named center, which defines the geometric center of the pouring circle. Based on this center point, the auxiliary variables bottom, right, top, and left are computed and define the key waypoints of the circular pouring trajectory. The radius of the pouring circle is specified by the variable radius, which can be adjusted to match the brewing setup. For the 1 cup V60 configuration used in this project, the radius is set to 0.029.

During execution, an outer loop iterates over the defined number of pouring rounds. For each round, the robot first moves to the center of the pouring position. A second, inner loop then executes the circular pouring motion. This motion is divided into two segments: first, the lower half of the circle is traced by moving from the center to the left position and back to the transition point for the upper circle; second, the upper half of the circle is executed by moving to the right position and returning to the starting point of the lower circle. This sequence results in a smooth, continuous circular pouring motion.

The duration of this inner loop is configurable within the program and is set according to the desired coffee draining time. Finer grind sizes generally require longer pouring times due to slower water flow through the coffee bed, whereas coarser grinds drain more quickly. The underlying objective is to select a combination of grind size and pouring duration that achieves a targeted brew ratio.

In the presented setup, the brewing parameters are chosen to achieve a ratio of 250 ml of water to 15 g of ground coffee within a total brewing time of approximately two to three minutes. The specific grind size used for this configuration is documented on the main project page.
