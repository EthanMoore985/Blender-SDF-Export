Exporting SDF Models from Blender with STL Meshes

This guide will walk you through setting up Blender to export SDF (Simulation Description Format) models with STL mesh files, and troubleshooting common issues.

Overview

This process is particularly useful for robotics and simulation environments like Gazebo or DART. The script provided will export:

An .sdf model file representing the structure and joints of your model.

.stl mesh files representing the visual and collision geometry of your model.

Prerequisites

Blender 4.x (Tested on 4.3.2)

Python knowledge (Optional but helpful)

Step 1: Install Blender and Setup Environment

Download and install Blender from blender.org.

Open Blender and create your 3D model.

Save your Blender project file (.blend) to a known directory (e.g., Documents/Octocopter.blend).

Step 2: Enable STL Export Add-on

Blender uses a built-in add-on to export STL files. However, sometimes this add-on might not be enabled by default.

Open Blender.

Go to Edit > Preferences > Add-ons.

In the search bar, type "STL" or "Import-Export STL".

Check the box next to Import-Export: STL format.

Click Save Preferences.

If you cannot find the add-on, manually install it as described below.

Manual Installation (If STL Export is Missing)

Download the STL add-on from the Blender Add-ons GitHub repository.

Extract the folder io_mesh_stl.

Move the folder to your Blender installation directory:

C:\Program Files\Blender Foundation\Blender 4.x\scripts\addons\

Restart Blender.

Enable Import-Export: STL format in Preferences as described above.

Step 3: Load the Export Script

Open Blender.

Go to Scripting workspace.

Create a New Script.

Paste the export-sdf.py script into the editor. (Assuming you have the provided script for exporting SDF).

Click Run Script.

Step 4: Prepare Your Model

Create and name your meshes for each part (e.g., link_01, link_02).

Create empties (preferably of type arrows) to represent joints.

Assign the joints to their parent and child links using the custom properties panel provided by the script.

Step 5: Export the SDF Model

Select the root link of your kinematic tree.

In the Constraints Properties tab, under Simple Kinematics, click Export using this object as root.

This will generate:

An .sdf file in the same directory as your .blend file.

A subfolder mesh_stl containing all exported .stl meshes.

Common Errors & Solutions

Error: PermissionError: [WinError 5] Access is denied: 'mesh_stl'

Cause: The script is trying to create the mesh_stl folder in a restricted location.

Solution:

Save your .blend file in a user-writable location (e.g., Documents or Desktop).

If you still face this issue, run Blender as Administrator:

Right-click the Blender icon → Run as Administrator.

Error: AttributeError: Calling operator 'bpy.ops.export_mesh.stl', error: could not be found

Cause: The STL Export Add-on is not enabled.

Solution:

Enable Import-Export: STL format in Preferences > Add-ons.

If it's missing, manually install it (see Step 2).

Additional Tips

Ensure that your model is properly structured with clear naming conventions.

Use Ctrl + A > Apply All Transforms to ensure correct positioning and scaling before exporting.

Check the console (Window > Toggle System Console) for any additional debugging information.
Resources

SDF Format Documentation

Blender Python API Documentation

Blender Add-ons Repository

License

This guide and the related scripts are provided under the MIT License.


