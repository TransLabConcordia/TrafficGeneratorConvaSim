TrafficGeneratorConvaSimu
Generate traffic from Excel-format trajectory data in a VR platform (Unreal Engine)

The TrafficGeneratorConvaSimu plugin allows you to import trajectory data from .csv files and automatically move vehicles in your Unreal Engine (UE) scene along those paths. It’s designed for use in virtual reality (VR) simulation environments, such as traffic research platforms.

1. Installation
Download the Plugin

Download TrajectoryConvaSimu.rar.

Extract it into your Unreal Engine project’s Plugins folder:

javascript
Copy
Edit
<YourUEProject>/Plugins/
Rebuild the Project

After copying, generate and build your project again.

When the build completes, you will see the new actor class appear under your C++ Classes folder inside the UE Editor.

<img width="586" height="316" alt="1" src="https://github.com/user-attachments/assets/fe0403ea-76a8-4e2d-8d21-124878474fef" />



<img width="1265" height="775" alt="2" src="https://github.com/user-attachments/assets/5da4f19f-9ba9-4e1e-a5ba-9db0b6ab9baa" />


2. Adding the Actor to Your Scene
Open your UE project in the editor.

Locate the actor in the C++ Classes section.

Drag and drop the actor into your scene.

3. Setting Up the Trajectory
Prepare Your CSV File

Your trajectory must be saved in .csv format.

The columns in your .csv should follow the required structure:

| time | x | y | z | speed |
(Example structure — see image in repository for reference)

Import the CSV into UE

Drag the .csv file into the UE Editor’s Content Browser.

Assign CSV to the Actor

Select your placed TrafficGeneratorConvaSimu actor in the scene.

In the Details panel, find the CSV File Path field.

Enter the file path or use the UE file picker to assign your .csv file.

4. Assigning the Vehicle Actor
Choose a Vehicle Actor

You can use any vehicle actor from the Unreal Engine Marketplace (free or paid).

Assign It as Target

In the actor’s Details panel, set the Target Actor field to the vehicle you want to move along the trajectory.


<img width="1079" height="345" alt="3" src="https://github.com/user-attachments/assets/33d011b5-5a71-4559-a5c1-a04bf7784c49" />

5. How Movement is Triggered
In the default setup:

The vehicle starts moving when it detects a collision with another actor.

This is handled in C++ by checking for collisions and triggering movement once a collision occurs.

To start movement automatically at game start:

Move the relevant parts of the code from the collision handler into the BeginPlay() function of your actor’s C++ code.

6. Example: Collision-Triggered Movement
In the included setup:

The ego vehicle has a collision box.

When the ego vehicle’s collision box collides with a surrounding car’s collision box, the surrounding car starts following its assigned trajectory.

7. CSV Format Requirements
Your .csv trajectory file should have columns similar to this example:

time (s)	x (cm)	y (cm)	z (cm)	speed (m/s)

(Replace with your own data — see repository image for exact format.)




<img width="249" height="273" alt="4" src="https://github.com/user-attachments/assets/eab377e4-c629-446d-9851-75297e355522" />


