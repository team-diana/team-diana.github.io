#Development guidelines 

## New ros packages
* The name of the package must start with the rover name and the different words must be separated with _
* The name of the node must be the same but without the rover name
Remember to follow the ROS standards
### Example:
Package: t0r0_driving_gui
Node: driving_gui

## New git repos
* If it's a ros package follow the "New ros packages" instructions
* If it's a repo containing code for a specified rover put the rover name before the repo name (t0r0_driving_core)
* If it's a general repo use a useful name
* **Remember the Readme.md file**, it's very useful for other team members