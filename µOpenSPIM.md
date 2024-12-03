
<a href="https://github.com/openspim/micro-OpenSPIM" target="_blank" title="µOpenSPIM-Github Site"><img src="https://openspim.org/images/%C2%B5OS_Logo.png" width="200"></a> is an intuitive new graphical user interface (GUI) for OpenSPIM users, which relies on [µManager](https://micro-manager.org).

## Features of µOpenSPIM
-   A complete overhaul of the GUI has been made including simple graphic visualizations and an improved control over Picard’s 4D-stage
-   A user-friendly way of setting up multiview time lapse recordings with several positions and the option to acquire periodic and sporadic intervals with optional breaks during time-lapse recordings
-   A quick save function for nearly all acquisitions settings to save time in case an imaging session is interrupted or a similar session will take place at another time
-   Different saving formats allow acquisition as single plane tiff files, whole stacks or in n5 format, which is optimised for browsing through big data.
-   ArduinoUNO support for basic but efficient control of several connected hardware devices so that OpenSPIM users can quickly benefit from improved image acquisition speed and acquisition accuracy
-   An option for on-the-fly maximum intensity projections
-   A Picard Stage calibration feature to correct rotational inaccuracies and to improve the 4D-USB stage control
-   A tested drift-correction functionality with new options that can help with keeping a drifting sample within the field of view during long term image acquisition
- And more to come...

## µOpenSPIM requirements
-   All hardware components of an OpenSPIM system (Laser, Camera, Stage, etc.) have to be pre-configured with µManager's Hardware Configuration Wizard using Version 2.0 gamma (nightly build 04 May 2021) on a Windows7/10 computer.
-   µOpenSPIM has been tested with Picard's USB 4D-Stage in mind. Using different 4D-Stages should work but could lead to unexpected behaviour.

## How to set up µManager before using µOpenSPIM?
-   Click [here](/µOpenSPIM_µManager-configuration) if you have never created a working .cfg file with µManager before or/and want to get guidance on configuring multiple cameras, pixel size calibration and configuring an ArduinoUNO board for µManager.

## Installation and start-up of µOpenSPIM
-   Right now, µOpenSPIM is in its beta stage and works with µManager 2.0.0 20210503 for Windows (nightly build 3rd May 2021).
-   See also our [µOpenSPIM-Github Site](https://github.com/openspim/micro-OpenSPIM).
1.  Please [download](https://download.micro-manager.org/nightly/2.0.0-gamma/Mac/Micro-Manager-2.0.0-gamma1-20210503.dmg) and install the [64-bit](https://download.micro-manager.org/nightly/2.0.0-gamma/Windows/MMSetup_64bit_2.0.0-gamma1_20210503.exe) build of [µManager](https://micro-manager.org/) and follow its *Hardware Configuration Wizard* to create a functional configuration file (.cfg) that allows µManager to control the OpenSPIM hardware. On the first time startup of µOpenSPIM users will be asked to select the file location of µManager.
2.  Download µOpenSPIM for <strong>[Windows 64-bit](https://github.com/openspim/micro-OpenSPIM/releases/download/v1.0.11/OpenSPIM_setup_1.0.11.exe)</strong> or <strong>[MacOSX](https://github.com/openspim/micro-OpenSPIM/releases/download/v1.0.11/OpenSPIM-1.0.11.dmg)</strong> and follow the installation guide.

3.  In the starting window multiple µManager configuration files can be added, removed and selected. Click *Add .cfg file* to add and then select your working µManager configuration file ending with .cfg. Then click the *Start* button. After loading the hardware µManager should now be ready for use.

## Getting familiar with µOpenSPIM's GUI
-   The GUI of µOpenSPIM can be arranged in many ways and then saved and restored if needed.</br>
Click <a href=\µOpenSPIM_GUI>here</a> for more information and help.

## Acquisition with µOpenSPIM 
The process of acquiring images ranges from snapping a single image to recording overnight (or longer) time lapses of samples from N different angles.

## Acquiring a Single Image
<img src="https://openspim.org/images/µOpenSPIM_single-image.png" width="100"></br>
 To acquire a single image with µOpenSPIM:

1.  Navigate the 4D stage to the location you want to image.
2.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add current position</span>&nbsp;to add this plane to the position list. 
3.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add TP</span>&nbsp;and set both, the number of time points (TP) and the interval, to 1.
4.  Add at least one channel to the Software Controlled Channels list or select one of the Channels that are available in the Arduino Controlled Channels list. Don't forget to set the desired exposure time of each channel.
5.  You may specify an Output directory&nbsp;<img src="https://openspim.org/images/specify_dir.png" width="20">&nbsp;if you would prefer the image be written straight to disk, rather than opened in µManager using the computer memory. A metadata.txt file of all acquisition settings will also be saved into the Output directory.
6.  Finally, click <span style="color:#008000; background-color:#DCDCDC; font-weight:bold">Acquire</span>&nbsp;to capture a single or multi-channel image.

## Acquiring a Stack
<img src="https://openspim.org/images/µOpenSPIM_single-stack.png" width="100"></br>
A stack is a sandwich of many image slices of different focus levels of the sample with a defined beginning and end. To set up a stack requires to move the Z stage.

1.  Navigate to the sample location where the Z stack should begin.
2.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Z-start</span>&nbsp;and the current Z position will now show up next to the button.
3.  Navigate to the sample location where the stack should end.
4.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Z-end</span>&nbsp; and the current Z position swill show up once again next to the button.
5.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Go to centre</span>&nbsp;and check if the Z Stage ends up in the middle of the stack. This is a good way to know that the Z stack has been set correctly.
6.  Specify the Z-Step Size (in μm).
7.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pos.</span>&nbsp;to add the newly defined Z stack to the position list on the left. It will also include the X, Y, and R positions.
8.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add TP</span>&nbsp;and set both, the number of time points (TP) and the interval, to 1.
9.  Add at least one channel (either Software Controlled or Arduino Controlled) to the Channels list and set each channel's exposure time.
10. Though a single stack can easily fit into the memory, it is recommended that you specify an Output directory&nbsp;<img src="https://openspim.org/images/specify_dir.png" width="20">&nbsp;so the stack is saved to the disk. A metadata file of all acquisition settings will additionally be saved into the Output directory.
11. Optionally:
    -   turn on <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Show/Save Maximum Intensity Projections of each TP</span>&nbsp;to receive a Maximum Intensity Projection (MIP) after the stack has been fully acquired. The MIP will be saved into its own sub-folder within the Output directory.
12. Click <span style="color:#008000; background-color:#DCDCDC; font-weight:bold">Acquire</span>&nbsp;to capture the defined stack.

## Single-Plane Time Lapse
<img src="https://openspim.org/images/µOpenSPIM_time-lapse.png" width="300"></br>
 To acquire a time lapse of a single plane, set up the recording exactly as if you were going to record only one image.

1.  After clicking <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add TP</span>&nbsp;specify how often the plane should be imaged and set its recurring time interval (in seconds, minutes, hours or days).
    - Optionally you can add acquisition breaks by clicking <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pause</span>. Then specify the length of the acquisition break and click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add TP</span>&nbsp;to continue with a new time lapse recording after the acquisition break.
2.  Add at least one channel (either Software Controlled or Arduino Controlled) to the Channels list and set each channel's exposure time.
3.  &nbsp;<img src="https://openspim.org/images/specify_dir.png" width="20">&nbsp;Clicking this button will allow you to specify an Output directory. A metadata file of all acquisition settings will additionally be saved into the Output directory.
4.  Optionally:
    -   Enable Anti-Drift: choose between Phase Correlation (functionality is based on the 3d-stack with x, y, and z coordinates) or Centre of Mass (functionality is only based on x, y coordinates). Note that beads surrounding the sample might affect the Anti-Drift.
    -   Select a region of interest (ROI): Select a ROI with the Rectangle tool in the µManager's preview window, which will pop up when you click *Live View*. Then click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Apply</span>.
    -   Enable Binning: Choose one of the binning options and press apply.
5.  Click <span style="color:#008000; background-color:#DCDCDC; font-weight:bold">Acquire</span>&nbsp;to begin the time-lapse recording.

## Single-View Time Lapse
<img src="https://openspim.org/images/µOpenSPIM_4d-time-lapse.png" width="300"></br>
 To record a single view/stack of a sample over time:

1.  Navigate the 4D-stage to the location you wish to acquire images and specify the beginning and the end of the Z stack and the Z-Step Size (in μm) as described above. In the Picard 4D-stage the minimum Z step size is 1.524 µm. 
2.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pos.</span>&nbsp;to add the newly defined Z stack to the position list on the left and specify how often the stack should be imaged and set the recurring time interval (in seconds, minutes, hours or days).
3.  &nbsp;<img src="https://openspim.org/images/specify_dir.png" width="20">&nbsp;Clicking this button will allow you to specify an Output directory. A metadata file of all acquisition settings will additionally be saved into the Output directory.
4.  Optionally:
    - Enable Anti-Drift: choose between Phase Correlation (functionality is based on the 3d-stack with x, y, and z) or Centre of Mass (functionality based on x, y). Note that beads surrounding the sample might affect the Anti-Drift.
    - Select a Region of interest (ROI): Select a ROI with the Rectangle tool in the µManager's preview window, which will pop up when you click *Live View*. Then click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Apply</span>.
    - Enable Binning: Choose one of the binning options and press apply.
    - Turn on <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Show/Save Maximum Intensity Projections of each TP</span>&nbsp;to receive a Maximum Intensity Projection (MIP) after the stack has been fully acquired. The MIP will be saved into its own subfolder within the Output directory.
5.  Click <span style="color:#008000; background-color:#DCDCDC; font-weight:bold">Acquire</span>&nbsp;to begin the multi-view time-lapse recording.

## Multi-View Time Lapse
<img src="https://openspim.org/images/µOpenSPIM_multiview-timelapse.png" width="300"></br>
To record multiple views of a sample over time:

1.  For each view:
    - Navigate the 4D-stage to the location you wish to acquire images.
    - Specify the beginning and the end of the Z stack and the Z-Step Size (in μm) as described above. In the Picard 4D-stage the minimum Z step size is 1.524 µm. 
    - Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pos.</span>&nbsp;to add the newly defined Z stack to the position list on the left.
2.  After clicking <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pos.</span>&nbsp;specify how often the stack(s) or view(s) should be imaged and set the recurring time interval (in seconds, minutes, hours or days).  Add acquisition breaks by clicking <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pause</span>&nbsp;and specify its length. Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add TP</span>&nbsp;to add new time lapse span which will continue after the acquisition break.
3.  &nbsp;<img src="https://openspim.org/images/specify_dir.png" width="20">&nbsp;Clicking this button will allow you to specify an Output directory. A metadata file of all acquisition settings will additionally be saved into the Output directory.
4.  Optionally:
    - Enable Anti-Drift: choose between Phase Correlation (functionality is based on the 3d-stack with x, y, and z) or Centre of Mass (functionality based on x, y). Note that beads surrounding the sample might affect the Anti-Drift.
    - Select a Region of interest (ROI): Select a ROI with the Rectangle tool in the µManager's preview window, which will pop up when you click *Live View*. Then click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Apply</span>.
    - Enable Binning: Choose one of the binning options and press apply.
    - Turn on <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Show/Save Maximum Intensity Projections of each TP</span>&nbsp;to receive a Maximum Intensity Projection (MIP) after the stack has been fully acquired. The MIP will be saved into its own subfolder within the Output directory.
5.  Click <span style="color:#008000; background-color:#DCDCDC; font-weight:bold">Acquire</span>&nbsp;to begin the multi-view time-lapse recording.


## Acquisition Controls
The following image will introduce you to the location of all available controls to set up an imaging session.</br>
For a more detailed description follow this link: <strong>[Detailed Acquisition controls for µOpenSPIM.](https://openspim.org/images/%C2%B5OpenSPIM_Acquisition_08-03.jpg)</strong>
<figure>
  <a href="https://openspim.org/images/%C2%B5OpenSPIM_Acquisition_08-03.jpg" target="_blank" title="µOpenSPIM-Acquisition panel"><img src="https://openspim.org/images/%C2%B5OpenSPIM_Acquisition_08-03_50percent.jpg"></a>
<figcaption>Acquisition Controls of the µOpenSPIM GUI (A-I) with the Picard 4D-stage controls on the top right (J) and the Console window on the bottom right  (K). For a higher resolution image click <a href=\images/%C2%B5OpenSPIM_Acquisition_08-03.jpg>here.</a>
</figcaption>
</figure>  

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(A)</span> **Positions**</br>
This table shows the list of predefined positions, which will be acquired at each time point. There might be multiple positions or just one. A position is defined by the location where the four motorized stepper motors (X, Y, Z, and R) will move before acquiring an image or stack at a given time point.</br>
In case of an 3-dimensional stack, the Z stage will have three location values: Z start and Z end location values, both defining the total volume of the stack, and the Z step size value, which specifies the total amount of slices within this volume, whereby each slice is one image.

1.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add position:</span>&nbsp;Clicking this button will add a row to the end of the table with the current X, Y, Z and R coordinates.
2.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Delete position:</span>&nbsp;Clicking this will remove a highlighted row from the table. You can click and drag rows and move them up and down by using the arrows at the end of the row.
3.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Update position:</span>&nbsp;Clicking this button will update the selected position according to the current 4D-stage positions (X, Y, Z, R).

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(B)</span> **Define Z-stacks**</br>
Here the beginning and the end of a new stack together with its Z step size can be specified using the Z stage. One has to first find the sample and a centre it in the field of view. By navigating through the sample along the z-axis the beginning and end of a z-stack is specified. 
1. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Z-start:</span>&nbsp;Clicking this button will mark the current z stepper motor position as the beginning of a desired z-stack.
2. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Z-end:</span>&nbsp;Clicking this button will mark the current z stepper motor position as the end of a desired z-stack.
3. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Go to centre:</span>&nbsp;Clicking this button will move the stage Z into the centre of the defined z-stack.
4. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Z-stack:</span>&nbsp;Clicking this button will add a row to the end of the positions table that will include the X, Y, and R positions together with the two z-stack positions (Z-start and Z-end) and the Z step size value.</br>
-   It is possible to manually change any positional values by double-clicking on one of the positional entries. Note that this can be done during an ongoing imaging session.
5. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">New Z-stack:</span>&nbsp;Clicking this button will clear all previously locked Z-stack values in order to define a new Z-stack.</br>
-   It is possible to manually change any positional values by double-clicking on one of the positional entries. Note that this can be done during an ongoing imaging session.

In order to overwrite all positional values with the current positions of the stepper motors simply select any previously created position entry and press the “Update position” button.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(C)</span> **Time points**</br>
This table includes the information how often the predefined positions should be acquired. A time point can be specified once or many times for long term time lapse recordings. In case 3-d stacks are acquired across a given period of time, the imaging process is referred to as 4d-Microscopy.
1. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add TP:</span>&nbsp;Clicking this button will add a row to the end of the time points table where the number of time points and their recurrent intervals can be specified.
2. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pause:</span>&nbsp;Clicking this button will add an acquisition break to the end of the time points table. 
3. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Delete TP:</span>&nbsp;Clicking this will remove any highlighted row from the time points table.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(D)</span> **Channels**</br>
A typical channel is a laser of a given wavelength illuminating the sample during acquisition. In case an Arduino UNO is in control of one or several lasers, they all must be wired to one of the digital output pins. It is possible that a channel represents a different device other than a laser. Alternatively, lasers can also be controlled by the Software, which in our case is µManager. Do find out more about Software versus Hardware controlled imaging, click [here](/µOpenSPIM_SoftwareVSHardware).
1. **Software controlled** Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add channel</span>&nbsp;to add a new channel to the table. Several channels can be added to the table. 
-   Click into the drop-down menus to change Camera and the correct Shutter for the intended laser line.
- Double click on the exposure value of any added channel to change it.
2. **Arduino Controlled:** Simply select one or several of the available channels (**Pin8** to **Pin13**) that are under the control of the Arduino-Shutter. Channel Names can be changed in the Arduino UNO configuration table.
    - Double click on the exposure value of any added channel to change it.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(E)</span> **Summary**</br>
This table provides a summary of the final imaging session with its current settings.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(F)</span> **Saving options**</br>
1.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Save images:</span>&nbsp;If ticked acquired images will be saved to the hard disk. 
2.  &nbsp;<img src="https://openspim.org/images/specify_dir.png" width="20">&nbsp;Clicking this button will allow you to specify an Output directory.
3.  &nbsp;<img src="https://openspim.org/images/open_dir_v2.png" width="20">&nbsp;Clicking this button will open the specified Output folder.
4.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Saving format:</span>&nbsp;
    - Choose <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Single Plane TIFF</span>&nbsp;to save every image individually.
    - Select <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">OMETIFF Image stack</span>&nbsp;to save every time-point as an individual stack including all channels as an ometiff file.
    - Select <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">N5 format</span>&nbsp;to save your acquired data in the N5 format, which allows images to be available in multiple resolutions and can be written in parallel. More info on N5 can be found [here.](https://github.com/saalfeldlab/n5)
5.  <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Show/save Maximum intensity Projections of each TP:</span>&nbsp;We advise to tick this option for long time-lapse recordings. It can be very useful to have a first impression of how well an imaging session goes or went, particularly if large SPIM data is acquired where generating MIPs after imaging is completed can be very time-consuming.
6.  Here notes can be written down, which will be saved as an additional Note.txt file into the Output directory.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(G)</span> **Save/Load settings**</br>
All input settings created by the user including Positions, Time points and Channels can be saved here and loaded again at a later time point.
1.  Click <span style="color:#008000; background-color:#DCDCDC; font-weight:bold">SAVE</span>&nbsp;to save all acquisition settings as an .xml file.
2.  Click <span style="color:#FFA500; background-color:#DCDCDC; font-weight:bold">LOAD</span>&nbsp;to load previously saved acquisition settings.
3.  Click <span style="color:#FA8072; background-color:#DCDCDC; font-weight:bold">CLEAR</span>&nbsp;to clear the Acquisition panel from all settings and tables.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(H)</span> **Acquisition**</br>
After all positions and number of time points have been specified, it's almost time to start imaging. However, there are still a few options worth considering before starting the acquisition process such as ROI, Anti-Drift and Binning. It's also worth checking one more time if the correct saving format has been chosen and whether Maximum Intensity Projections should be generated on the fly.
1. <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Anti-Drift:</span>&nbsp;Click the Anti-drift tab to enable it with the aim to prevent the sample from leaving its initial predefined position. One can choose between Phase Correlation (whereby entire volume of a 3d-stack is taken into account) or Centre of Mass (whereby drifts are only corrected in x, y but not in z). Note that high concentrations of fluorescent beads surrounding the sample may disarrange the Anti-Drift functionality.
2. <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">ROI:</span>&nbsp;Within this tab a region of interest (ROI) can be specified and applied to the field of view of the camera. The region is specified in the preview window of µManager. Select the Rectangle tool and create a selection inside the preview window. The window will open up by clicking *Live view*. When the ROI is specified, click the <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Apply</span>&nbsp;button.
3. <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Binning:</span>&nbsp;Different binning options can be selected before acquisition, e.g. **2x2** or **3x3** binning. Higher Binning settings combines the charge of more pixels, which increases the signal to noise ratio (SNR) and results in higher camera frame rates but on the expanse of pixel resolution.
4. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Live:</span>&nbsp;Clicking this button will toggle the camera into live view. The exposure values can be changed below.
5. <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Acquire:</span>&nbsp;Clicking this button will start the currently set up imaging session.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(I)</span> **Preview of imaging session**</br>
Here a simple schematic overview is given showing the current list of time points that have been set up.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(J)</span> **Stage**</br>
Here you can move the four stepper motors of the 4D-stage Stages (X, Y, Z, R), calibrate the rotational stepper size (R Stage), save and load current positions and inverse the axis of the x and y stage, which might be crucial for the Anti-Drift to work correctly.
    
1.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Save current position:</span>&nbsp;Click this button to save the current position of the stage. It will be added to a list.
2.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Load location:</span>&nbsp;Click this button to Load a previously saved stage position from a list.
3.  <span style="color:#000000; background-color:#DCDCDC; font-weight:bold">Indicate angles:</span>&nbsp;Indicate here the number of angles you wish to acquire during a single time-point. The angles will then be indicated above the rotational stage (Stage R).
4.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Homing</span>&nbsp;on one of the four Stages to move the stepper motor back to its home position.
5.  Click <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Stop</span>&nbsp;to immediately stop a stepper motor.
6.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Calibrate:</span>&nbsp;Click this button to calibrate the R Stage in case the 360 degrees do not correspond to a full revolution of the sample holder.
7.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Add Pos.</span>&nbsp;Clicking this button will add a row to the end of the Position table using the current X, Y, Z and R coordinates.
8.  <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Go back to the last used position</span>&nbsp;Clicking this button will move the stage to the previous position.

<span style="color:#FF00FF; background-color:#DCDCDC; font-weight:bold">(K)</span> **Console**</br>
The console window can be useful to see what is going on in the background of the plugin and to spot error messages.
1.  Clicking <span style="color:#1E90FF; background-color:#DCDCDC; font-weight:bold">Clear</span>&nbsp; will delete all written content.
    
