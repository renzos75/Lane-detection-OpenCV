# Lane-detection-OpenCV
code snippet using python that detects a sharp change in gradient by taking an image, converting it to grayscale, then outlining the portions of the image that has the highest rate of change between light and dark
<br>
<br>
## Note
This is a python Program so you will not be able to run this project without first install the most recent version of python(3) onto your PC.
<br>
<br>
<br>
<br>
# Installation
first, in order to install python you must firt download <a href="https://www.anaconda.com/distribution/">Anaconda</a>, this will install the most recent version of python (make sure to select the correct OS) once installed open "Anaconda Prompt" and Run;
##### python -- version

This should display the version of python you installed with anaconda.
<br>
Once you've done that Run;
##### pip install opencv-contrib-python

From there you should have python installed and the opencv library installed as well. You can input the code into any IDE you use that reads python.


# Running script
the file name in the Repo is "lanes.py" for the sake of keeping things consistant you should keep that name the same. When you want to run the program, open <strong>Anaconda Prompt</strong> and "change directory" to where the "lanes.py" file is saved. 
<br>
For example;
<br>
<br>
If "lanes.py" is located in the desktop run:
##### cd desktop

Then run:

##### python lane.py
this will run the script

## Note
make sure you keep the image file and the mp4 file in the same folder as "lanes.py" or your image and/or video won't load. 
<br>
<br>
<br>
# Using other photos/Video
In "lanes.py" you will find.
<br>
<br>
def region_of_interest(image):<br>
    height = image.shape[0]<br>
    polygons = np.array([<br>
    [(200, height ), (1100, height), (550, 250)]
    ])<br>
    mask = np.zeros_like(image)<br>
    cv2.fillPoly(mask, polygons, 255)<br>
    masked_image = cv2.bitwise_and(image, mask)<br>
    return masked_image<br>
<br>
this sections defines the what part of the image or video to look for lane lines. Let me first explain the code is looking for a sharp change in brightness, so on a black road the white lines will be read as a sharp change in brightness. but as you can tell there are multiple regions in the photo that have sharp changes in the brightness(the sky) so we want to restrict (mask) what exactly the image is being looked at for this project we are using a triangle as the boundary for the mask. If you want to use this code for a different photo or video file find;
<br>
<br>
 polygons = np.array([<br>
    [(200, height ), (1100, height), (550, 250)]<br>
    ])
<br>
<br>
edit the integers next to height and the (550, 250) this will change the position of the "triangle". And add another ordered pair in side the brackets to make the polygon into a square.
