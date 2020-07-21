# Traffic-Density-Detection
Traffic Density Detection can be used to estimate the traffic in a particular area and also detect any vehicles in the frame.

## Description:

## AIM:

To detect and count the no of vehicles from a CCTV feed so as to know what
the real time traffic situation is.

## TOOLS USED:

*Python
*OpenCV
## Screenclip

![alt text](https://github.com/premmody312/Traffic-Density-Detection/blob/master/outputs/output.gif)


## APPROACH:

OBJECT DETECTION:
    In order to count vehicles we first need to be able to detect them in an image. This is pretty simple for a human to pick out but harder to implement in the machine world. However, if we consider that an image is just an array of numbers (one value per pixel), we may be able to use this to determine what a vehicle looks like and what we'd expect to see when there isn't a vehicle there. For this we convert the image from RGB to HSV. 
   The Saturation and Value can be used to distinguish vehicles from the background.
   
We can use OpenCV to average between several frames and create our background image. Now that we have a background image, or an array of default/background values, we can use OpenCV to detect when these values go above a certain value (or 'threshold value'). We assume that this occurs when there is a vehicle within that pixel, and so use OpenCV to set the pixels that meet the threshold criteria to maximum brightness.


NOW THAT WE HAVE A BACKGROUND IMAGE, OR AN ARRAY OF DEFAULT/BACKGROUND VALUES, WE CAN USE OPENCV TO DETECT WHEN THESE VALUES GO ABOVE A CERTAIN VALUE (OR 'THRESHOLD VALUE'). WE ASSUME THAT THIS OCCURS WHEN THERE IS A VEHICLE WITHIN THAT PIXEL, AND SO USE OPENCV TO SET THE PIXELS THAT MEET THE THRESHOLD CRITERIA TO MAXIMUM BRIGHTNESS (THIS WILL MAKE DETECTING SHAPES/VEHICLES EASIER LATER ON)

The images above show the pixels that meet the threshold criteria (left) and the resulting shapes after setting those pixels to maximum value/brightness (right). Also highlighted (green) is gaps in our objects where dark areas (windscreens, grills etc) may not meet our threshold criteria. This could cause a problem later on so we try to fill in these gaps using the erosion and dilation functions from the OpenCV library.

Once we are happy with the shapes created, we must then check the shapes (or contours) to determine which are most like to be vehicles before dismissing those that are not. We can do this be implementing a condition where we are only interested in the detected contours if they are over a certain size

## CHALLENGES:  
        We need to adjust for the reference values depending on the angle of the videos. Vehicles are difficult to detect in night and if they are of dark shade as they match with the background colour. This can be improved by using haar cascades for detection. 

## CONCLUSION: 
        This traffic density detection application has a good accuracy in detecting vehicles.
