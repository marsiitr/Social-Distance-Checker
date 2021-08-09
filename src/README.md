<p align="justify">
  <h1>How to download Open-cv</h1>
  <p>
  
  * First we need to download Pycharm with the steps shown in the given link
  </p>
  
[Steps to download](https://youtu.be/MoeQlmeJnPg)

* After downloading Pycharm we have to download several packages from the "python packages" tab present at the bottom of Pycharm IDE screen.
* Now type the following packages on the search bar : 

          opencv-python
          numpy
          Tensorflow
          Keras
          Matplotlib
          Scipy 
* After downloading all these packages we are ready to go.. lets see how to code

<p align="justify">
  <h1>Code explained</h1>
  <p>
  We have done this project in two phases :
       
  * Social distancing detection(sdd)
         
  * Mask detection
  
  and then we have integrated both the parts. Lets see how to do social distancing detection part.
  
  <p align="center">
    <h2>Flowchart</h2>
    <img src="https://user-images.githubusercontent.com/88554453/128680650-2d9ebb1c-bd42-4700-bb3b-02f40b7d5a9c.jpg">
    </p>
 
 <p align="justify">
  <h2>Brief explanation of our sdd code</h2>
  <p>
  First we have to import necessary packages by using "import" funtion.
  </p>
  
  
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128681859-b1d2d090-c0cf-4727-9307-a709d17293b1.jpg">
    </p>
  
  
  After importing packages shown in above image we have downloaded several model files(model files are pre trained files for example, we have a file named centroidtracker which is used to pairup different objects which we can use directly in the code to make the code shorter).We can download these files from the src folder.
  
  [Model files](https://github.com/rahulgrandhi13579/Social-Distance-Checker/tree/main/src)
  
  First we need to capture the video using the opencv in built function, i.e cv2.VideoCapture. Now , as video is comprised of no of frames , so we need to extract the frames which is done with the help of while loop.
  
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128687734-59867c70-6cc3-4898-a484-33c689057cf4.jpg">
    </p>
  
  After extracting the frames we need to first detect the people and create bounding boxes around them. We will detect people from classes array which is based on pretrained model files. After detecting people we have to create bounding box with the help of numpy inbuilt function (np.array). Now to overcome noises in the bounding box we will pass this to non_max_suppression_fast function or we can pass this to inbuilt non_max_suppression function. 
  
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128689534-5c43e33e-47da-4972-bcf8-5cf48d5d3ac9.jpg">
    </p>
  
  
  After filtering out the noises , we will save the coordinates of the final bounding box(bbox in our code). Once we get the coordinates of each bounding box in a single frame we will calculate distance between every two bounding boxes using euler's distance formula and then we will compare it with threshold value which we have to calibrate according to camera's position. Initaially the colour of all the bounding boxes are green, if the calculated distance is less than the threshold value then colour will changes from green to red indicating that person is violating the social distancing.
  
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128695111-db6b3c90-dc63-48e3-9807-c5797b3e044e.jpg">
    </p>
  
  And for the display of no of violations we have only incremented our counter(ans) by one in the loop , i.e when we detect any violation(convertion of green box to red box) then the counter gets incremented by one.
  
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128696151-f8acb044-2a51-4955-8992-53dc8f5d593a.jpg">
    </p>

 After merging all the above steps the final code looks like:
 
[Social Distancing code](https://github.com/rahulgrandhi13579/Social-Distance-Checker/blob/main/src/social%20distancing%20code.txt) 

<p align="justify">
  <h1>Mask Detection</h1>
  <p>
  Now let's look into Mask detection part.
  
  First we have to import several packages like TensorFlow , Keras , imutils ,etc
  
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128701217-bc734cd5-b05d-4818-8666-8dcc5d94f36c.jpg">
    </p>  
    
  After importing the packages we will use inbuilt dnn(deep neural network) function to access the configure and weight of model files(which is pretrained and ML with hundred of images with mask and without mask).
  
[Model files](https://github.com/rahulgrandhi13579/Social-Distance-Checker/tree/main/src)
  
  After that we have to make bounding boxes around faces with the help of modelfiles and inbuilt numpy function(np.array) and then we will compare those faces with the help of modelfiles which consists of hundreds of images which differ by mask and according to that if the person has weared a mask then the colour of the bounding box will be green and the matching percentage will be shown above it otherwise the bounding box will be in red colour.
  <p align="center">
    <img src="https://user-images.githubusercontent.com/88554453/128704267-5c81d576-4972-4f68-9ffe-6e461c53cb2e.jpg">
    </p> 
  
  After completion of above steps the code for mask detection looks like:

  [Mask code](https://github.com/rahulgrandhi13579/Social-Distance-Checker/blob/main/src/Mask%20detection%20code.txt)
  
  Finally after merging the above codes our final social distancing and mask detection code looks like:
  
  [Final code](https://github.com/rahulgrandhi13579/Social-Distance-Checker/blob/main/src/Socialdistance_mask_detection.py)
  
  [Brief Video explanation](https://drive.google.com/drive/folders/14n7pwF_lQPZzoZWCOvFKJNiqEQ0wh_3i?usp=sharing)
  
  <p align="justify">
  <h2>Note</h2>
  <p> 
  In our final code we have worked on a sample video named alley, so to work on different videos 
   
  * First we need to save our desired video in the same folder in which our pycharm project is present.
  * Then in our python code we need to replace the alley by our desired video name in the "cv2.VideoCapture" section.
  * For using webcam we need to replace alley with 0 by removing double quotes.
  


