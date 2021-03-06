## 360˚ WebVR Virtual Tour Tutorial

### Introduction
The webpage you’re looking at is called a “GitHub repository,” and it contains the files you'll use to build the virtual tool. Look at the folder structure and mentally note the names of the the folders.

Once you have looked at them, let's get started.

### Create an NCSU Github account
If you do not already have an NCSU Github account, create one [here](https://github.ncsu.edu)

Log into your account.

### Fork the code repository
A fork is like a copy of someone else's code repository that you can make changes to without affecting the original repository.

Navigate to [https://github.com/smsejwan/360-tutorial](https://github.com/smsejwan/360-tutorial)

Click the "Fork" button in the top right of the page:
![](assets/fork.png)

You should now have this code repository in your own Github account at the following address (replace YOUR_USERNAME with your Github account name):

https://github.com/Your_Username/360-tutorial

### Create a Github page for your project
Click on Settings

Under Github Pages, click the dropdown menu under Source. Change to **master branch**

![](assets/pages.png)

This will create a new web page where you can see your gallery live!

### Learn to make your own gallery

Open this link in a **new tab** to see what your gallery currently looks like, replacing YOUR_USERNAME with your Github username:
https://pages.github.com/Your_Username/360-tutorial

![Incomplete gallery](/readme_files/incompletegallery.png "Incomplete gallery")

As you can see, it's not quite similar to the gallery we saw previously in the Google Cardboard.  
We just have 2 images here instead of 6.

So to fix this, we need to add the remaining 4 images to this page.

### Task 1: Add images to the assets folder
The first task is to upload the images you just clicked in the asset folder.

If you don't have images you can use these images from a Google Drive folder. Download these [360 images](https://drive.google.com/open?id=0B7icOoMjnbmPZDBjVFAycHN4a3c) to your Desktop to use them.

Open the [*assets*](https://github.com/Your_Username/360-tutorial/tree/master/assets) folder in your repository.  

![Select assets](/readme_files/assetsselect.jpg "Select assets")

Rename the images to something you can easily remember. (for example a.jpg, b.jpg, etc...)

Then click on ‘Upload files’ button.
![Upload files](/readme_files/upload.jpg "Upload files")

Upload all the images (i.e., 3.jpg, 4.jpg, 5.jpg and 6.jpg) that you just clicked or downloaded.

After you are done uploading the images to the ‘assets’ folder, go to the [gallery.html](https://github.com/Your_Username/360-tutorial/blob/master/gallery.html) in your repository.

Click on the edit button.
![Cick at edit in gallery.html](/readme_files/galleryselectedit.jpg "Edit gallery.html")

Add some code in here to be able to see the remaining images.

### Task 2: Add Assets for remaining images.
We place all our assets in one place for better performance.

Look at lines 16 to 24 in the gallery.html file for reference
![Line 16 to 24](/readme_files/Line16-24.png "Line 16 to 24")

We place asset files (i.e., the photos) between these bracketed phrases ```<a-assets> </a-assets>```

The code for adding an asset looks like this:
```html
<img id="first" src="assets/1.jpg">
<img id="second" src="assets/2.jpg">
```

We need to add assets for the remaining images that we just uploaded to our assets folder so that they look similar.

Go to gallery.html and start adding assets on line 19 in gallery.html file.

Note that each img id must be different. Use this pattern: For 1st image: id="first" and for the second image: id="second" etc.)

The src needs to show the location (in the assets folder) and name of the file: "assets/imagename.jpg" (Example: src=”assets/1.jpg”)

*Hint: You can look at the assets already added for other images at lines 17 and 18.*

When you've done this for the 4 new images, scroll to the bottom of the page and press the green commit button.


### Task 3: Add the curved-image components for remaining images.
We have now linked our images to our webpage, Our next task is to display them.
To display them, we need to add a line like:

```html
<a-curvedimage
id="one"
src="#first"
height="3"
radius="5"
theta-length="40"
rotation="0 280 0"
position="0 0.8 0">
</a-curvedimage>
```

**Id:** identifies this element uniquely.  
**Height:** is the height of image.  
**Radius:** is the radius by which you want your image to appear curved.  
**Theta-length:** is the length occupied by the image in a circle. Circumference of the circle is 360 and here we have 6 images, and we are giving a theta length of 40 to each and there is a distance of 10 degrees between each image to keep them separated.  
**Position:** We are placing our 1st image at the position “0 280 0” moving along the y axis, we reduce the degree 50 (40 degree is space occupied by each image + 10 degree for distance between each image) so the position of our *second image will be “0 230 0”* and similarly for *third image it will be “0 180 0”* and so on.  

Here the properties **“id”**, **“src”** and **“rotation”**  need to be changed for each image.

Refer to line 30 to 39 in gallery.html and add similar lines there.  
![Line 30 to 39](/readme_files/Line30-39.png "Line 30 to 39")

Remember Since you have linked the locations of these images using `<assets>`, the id specified in the assets and src in the component need to be same

Example: If your asset is:
```html
 <img id="second" src="assets/2.jpg">
 ```
 Then your corresponding curved-image should be:
 ```html
 <a-curvedimage id="two" src="#second" transparent="true" height="3"
 radius="5" theta-length="40" rotation="0 280 0" position="0 0.8 0">
 </a-curvedimage>
 ```

 See that id in assets is same as src in your curved-image component.
 Start adding code at line 38.

 Once you’ve changed the code in **gallery.html**, click on this link to make sure the images appears: https://pages.github.ncsu.edu/smsejwan/360-tutorial/gallery.html

 If Images do not appear we can help you troubleshoot.

### Task 4: Our next task is to add 360 image file for each image to Demo folder.

Go to https://github.com/Your_Username/360-tutorial/tree/master/demos

Here we have to create a folder for each 360 view.
As you can see there are already 6 folders created in this view.

We need to go to each folder and make two changes.
The first change is in /demos/1/assets/
Add your image that is the 1st image in your gallery.

The second change: Open https://github.com/Your_Username/360-tutorial/blob/master/demos/1/index.html
And add Assets for our image and change the corresponding component.
And make the necessary change on line 13 and 31 of the above file.

At line 13:
```
<img id="background" src="assets/1-bg.jpg">
```
Change 1-bg to the name of image you just added to the assets folder.

And at line 31:
```
 <a-sky src="#background" rotation="0 -130 0"></a-sky>
 ```
Make sure your id in line 13 is similar to your src on your line 31, in this case, id="background" and src="assets"

Here on line 31:
We are changing a component ``` <a-sky> ```
The sky primitive adds a background color or 360° image to a scene. A sky is a large sphere with a color or texture mapped to the inside.

### Task 5: Add Link to the demos in gallery.html
Now We need to then connect these images to their 360 view. To do so we use Javascript.
You can refer the code below, How we link the first image to its 360 view
```
document.querySelector("#one").addEventListener('click', function() {
                window.location.href = "demos/1/index.html";
            });
```

As you notice, #one is the id you use while adding the components for the assets.
Now to finish the Task 5 you need to add similar code for the 4 images that you just added.

REMEMBER: That the id used in the curved-image component should be similar to the querySelector in your javascript.

Example: If your curved image component is ```html <a-curvedimage id="one" src="#first" transparent="true" height="3" radius="5" theta-length="40" rotation="0 280 0" position="0 0.8 0"> </a-curvedimage>```

 Then your javascript will be ```document.querySelector("#one").addEventListener('click', function() {window.location.href = "demos/1/index.html";});```

 Start editing gallery.html from line 105.

 Commit your changes.

 Now you can test your app here and check if all the links are working:[gallery.html](https://github.ncsu.edu/YOUR_UNITYID/360-tutorial/blob/master/gallery.html) in your repository.   

### Additional Work: Going Deeper with A-Frame
You have now worked with the major components of A-Frame to create your own gallery, and you can stop here. If you'd like to go deeper, let's take a look at some remaining concepts.

In our gallery.html
First part is the ***header section*** of our HTML file.
Here we are just linking our aframe.js
![header](/readme_files/head.png "header")

Next comes setting up ***A-scene***  

A scene is represented by the `<a-scene>` element. The scene contains all entities.  
Functions of A-scene are to:
- Add default canvas, renderer camera and lights
- Set up VREffect
- Add UI to Enter VR that calls WebVR API
![Ascene](/readme_files/ascene-assets.png "Ascene/assets")

The first section in a-scene is to add assets.  
We place all our assets in one place to preload and cache assets for better performance, as we did in our app to add all images in the assets section.  

Next we add all the things that we want to appear on our screen.
In our case we add all the image components.
![Image Components](/readme_files/image_components.png "Image Components")

Next is adding sky and light components and setting up the camera and cursor.  
**Sky:**  Sky component adds a background color or 360° image to a scene.  
**Camera:** Camera determines what the user sees. We can change the view of user by modifying the camera’s position and rotation.  
**Cursor:** Cursor provides basic interactivity with a scene on devices that do not have a hand controller. The default appearance is a ring geometry. The cursor is usually placed as a child of the camera.  
![Cursor](/readme_files/cursor.png "Cursor and sky Info")

Then we finally add our javascript to load VR mode automatically and link images
![Auto enter Vr Script](/readme_files/js_script.png "Auto-enter Vr Script")

### You can extend this app
https://pages.github.ncsu.edu/smsejwan/a-frame-gallery/homepage.html
