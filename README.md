# ROOM EIGENMODES SIMULATOR v1.1
![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/img/loading_screen_1.1.bmp)

Application developed using the Application Builder of COMSOL Multiphysics® v5.6 to calculate and evaluate the natural frequencies of rooms modeled in 3D.

------------

## Download and Installation
The executable version for Windows (only x64) can be downloaded using any of the following links:
- https://github.com/Ylio7/simulador-de-modos-propios/tree/master/exe
- https://bit.ly/3ifNOKw

Steps to follow:

1. Execute the file Room_eigenmodes_simulator_v1.1.exe.

1. If a Windows Smart Screen warning message appears when you start the program, choose More Info > Run Anyway.

1. If it is detected by Windows Defender, add the program to the allowed list.

1. If this is the first time the application is being executed, the COMSOL Multiphysics® runtime environment necessary to run the application will be downloaded. Terms and conditions must be accepted and choose the installation folder (it is recommended to leave the default one).

## Tools
The application starts with the geometric model by default (default.stl). A table containing a few of its natural frequencies is also showed.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/001.png?raw=true)

### Import model
It allows importing geometric models in .stl, .dwg, .dxf and other 3D CAD formats. It is recommended that models made in SketchUp to be exported in .stl format.

### SketchUp Online
Open the website https://app.sketchup.com/app to create room models using SketchUp software tools for free, to be later imported into the application.

### Plot geometry
Draws the geometric model in the plot area.

### Mesh
Draws the calculation mesh in the plot area.

### Resolutions
Allows increasing the resolution of the mesh and the angles between faces (the latter exclusively for .stl models).

### Contours
Allows to select and hide contours (faces). Useful for observing pressure zones and isocurves within the enclosure.

### Calculate
Calculates the eigenfrequencies based on two input parameters:

- Minimum amount of frequencies to calculate: the default value is estimated to cover until the Schroeder frequency.
- Calculate from: indicates the lower frequency, although it could be even lower depending on the dimensions of the enclosure. It is generally recommended to leave this value at 20 Hz.

Once the natural frequencies have been calculated, they are shown in the table to the right of the plot.

### Plot eigenmodes
Draw the pressure and isocurve maps using the color code shown on the right, which ranges from blue (minimum pressure areas), through white (cancellation areas) to red (maximum pressure areas). Enables the interactive controls below the chart, which allow the user to select the natural frequency to be displayed, play a pure tone of that frequency, control the behavior of the isocurves with a slider and select the number of levels to subdivide them.

### Export table
Exports the table of calculated natural frequencies to a .txt file.

### Generate report
Produces an automatic report based on the following input data:
- Title
- Author
- Company
- Date
- Version
- Summary


### Analysis worksheet
Opens an Excel worksheet that allows observing the distribution of modes and performing an analysis according to Bonello's criteria. For its correct use, in the first instance the natural frequencies must be copied to the clipboard using the corresponding tool in the results table.
Then, in the worksheet, the user must click on the Import Data button to carrying out the calculations and generating the necessary graphics for the analysis. A name must also be entered for the room. The results can be found in the Evaluation sheet.

### Schroeder frequency
The following information appears in the lower area of the application:
- Volume of the enclosure: automatically calculated.
- Reverberation time at mid frequencies Tmid : must be entered by the user.
- Schroeder frequency: with the Volume and Tmid data, the application calculates the cutoff frequency from which it is estimated that the wave behavior of the room is no longer relevant. **This frequency should be taken as an approximation, since it will also depend on the morphology of the room under analysis.**

### Pure tone player
Reproduces a pure tone at the selected natural frequency. 

## Practical example
### Importing geometric model
We proceed to use the Import model > STL tool and search for the conference.stl file inside the models/stl folder.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/002.png?raw=true)

When inspecting the model, a low quality is verified in the morphology of the curved surfaces. To improve this, the Resolutions tool should be used. Since the imported file is .stl, it is possible to increase the angular resolution between faces. Select the Extra high option and verify that the curves have been considerably improved.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/003.png?raw=true)

The resolution of the mesh can also be increased (which will increase the computation time). Generally, the default Normal should be used.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/004.png?raw=true)

It should be noted that the adjustment of these resolutions is not mandatory, it will depend exclusively on the complexity of the model. The calculation can be carried out directly after importing the model since the application will use the default resolutions (Normal).

With the mouse it is possible to interact with the geometry. The left button rotates the view and the right button moves the current plane. Pressing and holding the scroll wheel and moving the mouse up and down, you can zoom-in and zoom-out. Holding Alt + left mouse button rotates the model in the current plane. These actions can also be carried out with the upper controls of the graphic panel.

### Calculation
Once the model is imported, the value of the Tmid must be entered. For this example, we will use 0.90 seconds, so the Schroeder frequency will be 96.6 Hz. Next, click on Calculate and you see that the application recommends obtaining at least 45 frequencies to reach the Schroeder frequency . Without modifying these values, proceed to calculate.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/005.png?raw=true)

Once completed, observe that the eigenmode plot and the results table with the natural frequencies have been generated, which reach up to 105 Hz, thus covering the Schroeder frequency. To inspect within the room, some faces must be hidden using the Contours tool. Then, go back to Plot eigenmodes to continue the inspection.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/006.png?raw=true)

Adjust the view, select the frequency of 49.3 Hz, a level division of 20 and interact with the slider to observe the behavior of the isocurves.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/007.png?raw=true)

Finally, we proceed to carry out the eigenmode distribution study and the analysis according to the Bonello criterion. For this, copy the content of the results table to the clipboard with the corresponding tool. Then, click on Analysis Worksheet. Once open, click the Import Data button to import the frequencies. Next, name the room as "Conference" and we observe in the Evaluation sheet the following results:

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/008.png?raw=true)

As can be seen, the study reaches up to the third octave band of 100 Hz, due to the cutoff by the Schroeder frequency. In this example, the mode distribution meets the Bonello criterion.

## SketchUp Online
Due to its simplicity and speed of drawing, it is recommended to make the models using SketchUp. It allows the models to be exported in .stl format to be later imported into the application. If you do not have this program, there is a free online version that allows you to design and model rooms.
Clicking on "SketchUp Online" icon will open the login page. You can create a Trimble account or connect with a Google or Apple account.

![](https://raw.githubusercontent.com/Ylio7/simulador-de-modos-propios/master/doc/img/009.png)

After the user is created, the home screen will appear. To start a new model, click Create New. It also allows you to open a .skp file stored on your computer.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/010.png?raw=true)

Once the room is modeled, it is good practice to select all the faces, right-click, and choose the Make Group option. In this way, by right-clicking again and selecting the Entity Information option, the volume of the room must be seen. Otherwise, the model will have to be reviewed since it has not been closed, which will cause errors when trying to import it into the application.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/011.png?raw=true)

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/012.png?raw=true)

Finally, to save the model on the computer, click on the drop-down menu and choose the option Download > STL. This file is the one that will be imported into the application.

![](https://github.com/Ylio7/simulador-de-modos-propios/blob/master/doc/img/013.png?raw=true)

## Contact
Eng. Agustín Ylio Arias

[agustin.arias@outlook.com](mailto:agustin.arias@outlook.com)

https://github.com/Ylio7

https://www.linkedin.com/in/agustin-ylio-arias/
