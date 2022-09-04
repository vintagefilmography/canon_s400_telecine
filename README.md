# canon_s400_telecine
  
This is one of the simplest telecine systems that is capable of creating a very good quality 8mm video.
The setup consists of a modified Canon S400 projector and the T3i Canon camera. The setup provides the 8mm film capture running at  up to 8 FPS and generates the video at 1280x972 resolution for the super 8 film. The R8 resoolution is lower but still good quality. It is to be noted that the Laowa macro lens is capable of higher resolution but it makes the setup much trickier.  More on that later in this doc.  
The purpose of this  readme is to provide the instructions to the user on how to modify the existing 8mm canon projector for the video capture directly into the camera.  
Similar to other projects of this type, this one also requires several modifications to the projector including the light change, and motor speed change. The diffecence is that the capture is run asynchronously i.e. the projector speed is not matched to the camera FPS but instead it runs at any speed within the 8FPS  ransge.
A simple posprocessing script takes care of multiple duplicate frames and black any frames. 

![image](https://user-images.githubusercontent.com/48537944/188248671-e75d3b05-5946-44a3-b92e-6547d1d91683.png)



##   Shutter Wheel Mod
The projector has three shutter blades. For this type of transfer it is necessary to remove two of the blades by snipping them off with the sheers. The blade that blanks out the film transition is left in.  
  
## Gate Mask Removal
This step is not completely necessary but it does provide film overscan and makes the film holes visible which some people like. The mask is a part of the S8/R8 switching mechanism. It is recommended to remove the mechanism and then cutting the masks out or bending them repetetively until they snap off. Be careful here because the components are very fragile.  


## Motor  Speed  
The motor speed should be reduced for 8 FPS operation. The unmodified projector low speed setting is still larger than 8  FPS. The speed reduction is achieved by installing a power resistor in series with the rheostat (speed adjust potentiometer).
![image](https://user-images.githubusercontent.com/48537944/188249456-6fbd4ef9-7bd1-4362-b24e-261fc122be61.png)  
Two 1000 Ohm, 10W resistors are used in series with the motor rotor to get the speed reduction.   
The bypass switch, labelled as 4FPS, bypasses the power resistors and gives the original speed. Can be useful for rewinding.  
The resistors are mounted on a custom aluminum heatsik as shown in the picture. The heatsink is secured down with a 4mm screw mounted on the top of the unit.

## Fan
The fan can be removed. It was required originally to cool the light and is no longer needed for the led light. For long scans a new fan can be attached to the back cover louvres to keep the resistors cool.  

## Light
The following light is recommended.  
https://www.amazon.com/gp/product/B07YSF3X8K/  
The mounting bracket design is located in the mechanical folder above.

## Camera Slider Mounting  
The following camera sider is used:  
https://www.bhphotovideo.com/c/product/193311-REG/Velbon_SUPER_MAG_SLIDER_Super_Mag_Slider.html
Two spacers are to be mounted underneath the slider mounting board. 
The board dimensions and the spacer stl file can be found in the mechanical folder.  


## Macro Lens
There are many out there that will do the job.  
Venus Laowa is a pretty good pick. It has more than enough magnification and good image quality and it is reasonably priced.
https://www.venuslens.net/product/laowa-25mm-f-2-8-2-5-5x-ultra-macro-2/  

## Assembly
Print out all of the parts from the mechanical folder. 
Attach the two spacers from the mechanical folder on the camera base board towards the edges of the board.

Drill two holes on the slider base board as shown in the following image:  
![image](https://user-images.githubusercontent.com/48537944/188285288-be6101ba-e37c-45ce-ac11-c686bb8371bb.png)
Drill the clearance holdes for the mounting bolts. Use 3/8"-16 bolts.  
Mount the slider onto the slider board.
![image](https://user-images.githubusercontent.com/48537944/188252379-55d57937-e123-4d6c-a2df-53946af8d5ef.png) 
Mount the slider and the slider base onto the main board. Drill a hole through the main board, spacer and the slider board as shown:  
![image](https://user-images.githubusercontent.com/48537944/188285610-f541bbd4-3889-4917-ad29-3ffe461c2acc.png)
If you plan to use the rubber bumpers under the main board then it is not necessary to drill a clearance hole for the 
mounting screw head. But if no bumpers are used a shallow clearance hole has to be drilled so that the screw head 
is not protruding through the bottom of the main board which could scratch the surface of the table or whatever stand you are using for the 
scanner. Size 10 bolt is adequate. A wingnut is also handy when it comes time to dismentle the unit. Adjust the wingnut tension so that the slider and the camera 
sit solid on the main board. A small vertical adjustment can be made by instrting a thin plastic card under the second spacer.
Mount the macro lens onto the camera.  
Mount the camera onto the slider.  
Turn the camera on. Position the projector close to the camera so that the film gate is visible and adjust the zoom so that the film gate covers most of the camera display. Adjust focus by turning the slider focus knob.   

## Camera  Settings
Make sure the battery is fully charged and the SD card is empty. 
Turn the camera on and make sure the film is in focus. Try to adjust the projector so that the film is on the   
righ hand side in the oreview window or on the HDMI monitor window. With the Laowa lens teh alignment between the  
camera and the projector is  not dead on which could cause the depth of files issues. So, positioning the film image to the   
right will mitigate the issue. Will not be perfect but pretty close to it.  
Set the F stop on teh lens to 2.8. If you notice some brurriness at the edges then set it to 4.  
Set ISO to 800.  
Adjust the shutter (wheel at the front of the camera) so that the image is bright enough.  
Ususlly anywhere between 200 and 300 should be OK.
Set the camera in video mode and set to 1920x1080/30FPS

## Operation

Load the film.  
Connect the camera HDMI port to a monitor. 
Turn the LED light on.  
Turn the camera on and press the live view button. 
Press Live View again to start recording.  
Run the projector and set the speed to minimum by using the speed knob at the front.  
Make sure that the resistor bypass switch is off.  
Once done with the recording, stop the camera by pressing the live view.  
Turn the camera off.  
Turn the projector off.  
Remove the SD card and copy the video to a PC.

## Post Processing  the video to a PC.  
The video will contain many frames with dark bands which are result of asynchronous operation.  
In another words the camera and the projector are not synched and the camera will pick up frames that contsin film transitions.
Additionally, since the frame rate of the camera is much faster than the projectors, there will be lots of duplicate frames.
It is easy to remove the duplicates and the transition frames by using the Avisynth remove_dups script.  
The first step in getting the the script working is to get Avisynth from:
http://avisynth.nl/index.php/Main_Page
Avisynth does not run as a standalone application. It is a tool that allows video editors and viewers to run the script.  
The script is essentially a text file that contains the avisynth commands for video processing.  
One video  tool that is very handy for video processing is called VirtualDub. 
In addition to basic video processing, VirtialDub reads the avisynth script as well.  
Download VirtualDub from here:
https://sourceforge.net/projects/vdfiltermod/files/
Run VirtualDub.  
Should get a dub window that looks like the following picture:
![image](https://user-images.githubusercontent.com/48537944/188292750-e048727a-57be-484a-8ec2-93b292a6a2a8.png)  

Using the avisynth script can get a bit tricky because there are some many plugins out there and you will usually  
run into a plugin missing error. That is why I put a complete scripts zip file in in the software folder. This contains  
the required plugins.  
Download the zip file and unzip it somewhere in your work directory. 


Go to the scripts directory and open up remove_dups.avs in any text editor like Notepad or any other text editor..
Change the clip source path to wherever the clip is stored.
#=============================================================================================
# Clip source.
#=============================================================================================

film = "F:\canon\clip1_raw.avi"  # source clip, you must specify the full path here  
  
Change the threshold:  
source= AviSource(film).assumefps(play_speed).trim(trim_begin,0).converttoYV12()  
trimming= framecount(source)-trim_end  
source1= trim(source,0,trimming)  
source2= AssumeTFF(source1)  
fc=Framecount(source2)  
source3 = GetDups(source2,mode=-2,threshold=30.0)  
source4 = Trim(source3,0,fc/3).coloryuv(autowhite=true)  
#Eval(film)  
  
Here it is set to 30. Lower threshold will have less chance of saving the bad frames but if it is too low it may remove some good frames.  
It is a good idea to check the frame count uo front by running teh projector at low speed and counting the frames for a minute or two to  
determine the frame rate and then run the complete reel and multiply the rate with duration. Alternatively a rough frame count can be obtained from the 
size of the reel.

Once done with the script, just drag the script file into the VirtualDub window.
After a minute or so the video first frame will be displayed.  
At that point, set the video compression in the video pulldown and save the video.
No further processing will be required, although soemtimes you may get a few blank frames.
If that happens run the remove_black_frames.avs script included here. 



