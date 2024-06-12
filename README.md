# RT_exam
```python
Initialization

Initialize picked_up_markers list
Initialize reference_token as None
Initialize ref_token_code as 0
Initialize threshold distances a_th and d_th

Define Functions

Define drive function (speed, seconds):
Set robot motors power to speed
Sleep for seconds duration
Stop robot motors

Define turn function (speed, seconds):
Set left motor power to speed
Set right motor power to -speed
Sleep for seconds duration
Stop robot motors

Define find_token function:
While no markers seen:
Turn robot right slightly
If no markers seen:
Continue loop
Print number of markers seen
Initialize marker as None
Initialize dist to a high value
Iterate over markers seen:
If marker is closer than dist and not picked or reference code:
Update dist, rot_y, and marker
If marker already picked or reference code:
Print "Already picked or reference"
Update marker
If no marker found or all markers picked:
Return None, -1, -1
Else:
Return marker, its distance, and angle

Define save_reference_token function:
Find a token using find_token
If a token is found:
Set it as reference_token
Update ref_token_code
Print "Reference token saved"
Else:
Print "No token found"
Define displace_token function:
Find markers in sight
Set found_it as False
Iterate over markers:
If marker code matches reference code:
Update reference_token and found_it
Break loop
If reference token found:
While token not displaced:
Get distance and angle to reference token
If distance is within threshold:
Release token and print "Released the token"
Set found_it to False
Break loop
Else:
Print "Not close enough"
Adjust robot's position towards reference token
Call avoid_obstacle
Recursively call displace_token
Else:
Print "Reference token not found"
Adjust robot's position
Call avoid_obstacle
Call displace_token recursively

Define detect_obstacle function:
Use specific sensors to detect objects
Differentiate obstacles from tokens based on:
Size
Shape
Marker presence
If obstacle detected:
Return True
Else:
Return False

Define avoid_obstacle function:
If detect_obstacle() returns True:
Stop robot
Turn left to avoid
Drive forward slightly to bypass obstacle

Main Code

Call save_reference_token
Print reference_token code
While true:
Get token, distance, and angle using find_token
If detect_obstacle() returns True:
Call avoid_obstacle
If no token seen:
Print "No token found"
Turn right slightly
Else, if token within grabbing distance:
Print "Found it"
If able to grab token:
Print "Gotcha!"
Displace token
Drive backward
Turn left
Append token code to picked_up_markers
Print picked_up_markers
Else:
Print "Not close enough"
Adjust robot's position towards token
If detect_obstacle() returns True:
Call avoid_obstacle
Adjust robot's position based on angle to token
If detect_obstacle() returns True:
Call avoid_obstacle
If all markers picked:
Print "Done!"
Break loop
```
