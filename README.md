# BIRD-Classifier-App
This Repository Contains the Projects Developed in Andriod(java).
The primary purpose of this project is to convert a tensor flow model into a tensor flow lite model and run it into the mobile application.

## Tech Stack

**LANGUAGE:** JAVA.

**LIBRARIES:** Tensorflow and Tensorflow lite

**Platform:** Andriod studio.


## FLOWCHART OF THE Implementation.

- ![Unknown](https://user-images.githubusercontent.com/85448730/208238358-77c25ba8-2fe6-4fb4-9ba6-ed312abd9477.png)


## Acknowledgements and Installation

 First I initialised the package name.
(package com.mohit.birdsclassification;)**


Second, I import the essential libraries Import libraries - It can include everything needed to build an app, including source code, resource files, and an Android manifest  like;


{
import androidx.activity.result.ActivityResultLauncher;
import androidx.activity.result.contract.ActivityResultContracts;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;
}


{ import com.mohit.birdsclassification.adapters.ProcessedImageAdapter;
import com.mohit.birdsclassification.databinding.ActivityMainBinding;
import com.mohit.birdsclassification.ml.Model;
import com.mohit.birdsclassification.utils.ViewAnimation;
}

{ Third I import the tf lite library to support the (Tensor image & label category)
import org.tensorflow.lite.support.image.TensorImage;
import org.tensorflow.lite.support.label.Category;
}

Here I define Activity binding to use for activity view binding it generates a binding class for each XML layout file in that module. An instance of a critical class contains direct references to all views with an ID in the corresponding layout.

![Picture 1](https://user-images.githubusercontent.com/85448730/208182882-64c4163d-66e5-4f86-b3dd-909a7e6aac51.png)

## DEPLOYMENT

Broadcast Receivers can send or receive messages from other applications or from the system itself. These messages can be events or intents.


![Picture 2](https://user-images.githubusercontent.com/85448730/208183134-b01b32c7-b861-4b16-b10b-9508af5467ea.png)


registerReceiver(broadCastReceiver, new IntentFilter(Intent.ACTION_BATTERY_CHANGED));  // for setting broadcast receiver for battery changes.

View animation to initialised animation in floating action button for 
Camera and image and viewer;



ViewAnimation.init(binding.fabCamera); // initialised animation in floating action button for camera.
ViewAnimation.init(binding.fabImage);// initialised animation in floating action button for image.
ViewAnimation.init(binding.fabFileViewer);


Creating a condition for checking;



**If 
{camera permission is allowed or not through the package manager if the camera permission is allowed then it will show in [Binding in image, camera and viewer]**

**Else 
{
It will show out in [Binding in the image, camera, viewer]**




**Here, I use  setOnClickListener;**
for binding in the image it means setonclicklistener will work 
Only opening file explorer for a particular image then it will launch the (intent).

**Here, I use  setOnClickListener;**
for binding in the camera for showing the camera fragment.



**Here, I use  setOnClickListener;**
for binding in the viewer for receiving a string and 
Put a for loop to recognise the length of the bird, the time elapsed, and battery level.



{
   receiveString = receiveString + "Bird Recognised: " + birdRecognised[i] + "\n";
   receiveString = receiveString + "Time Elapsed: " + timeElapsed[i] + "\n";
   receiveString = receiveString + "Battery Level: " + batteryLevel[i] + "\n";
}


  Here Activity will be launch means image launch and getting bitmaps 
From selected images in file explorer.


**Bitmap**
It is a class that represents a 2d coordinate system. The coordinate system moves to the right on the x-axis, and to the bottom on the y-axis. Each point in the coordinate system is called a pixel. A pixel is formed of bits, and bits represent the colour of this pixel. A pixel can be formed of 8, 16 or 24 bits ... The x-axis represents the width, and the y-axis represents the height.
**Why convert images into a bitmap?



if the image size is too large, it could produce an out-of-memory error. And it is not efficient to load bitmaps larger than the Image View canvas, (unless the Image View supplies custom functionalities such as pinch-to-zoom).
When the image is too large, or you wish to control its size for better memory optimisation, it must be decoded first into a Bitmap with reasonable metrics:



After this process image rendering will start for all the selected image will go through a loop too, Recognise the selected image and send them to the adapter.
private void imageRender(Bitmap[] urls)
for (int i = 0; i < urls.length; i++) {
   recognise(urls[i], i);
}



## Support And TensorFlow Trained Model

### Model.tflite;


<img width="671" alt="Screenshot 2022-12-17 at 12 58 11 AM" src="https://user-images.githubusercontent.com/85448730/208187582-ed3cb84e-d7e0-402b-99d0-84f5e24d755d.png">


## Optimizations

1. **Add TensorFlow Lite to the Android.**
Right-click on the package name in my case it is com. your package name or click on File, then New > Other > TensorFlow Lite Model. Select the model location where you have downloaded the custom-trained BirdsModel.flite earlier
Note that the tooling will automatically configure the module’s dependencies for you using ML Model binding and all requirements will be added to your Android module’s build. Gradle file.



 **In the end, you’ll see the following. The BirdModel.flite file has been successfully imported, and it displays high-level model information like input and output and some sample code to get you started.
After this, I used TensorFlow APIs for trained model recognition.
**Create inputs for references;



Model model = Model.newInstance(context);
**// Creates inputs for reference.**
long initial_time = System.currentTimeMillis();
TensorImage image = TensorImage.fromBitmap(bitmap);
Run the trained model to the inference and get the result in the highest probabilities.




**// Runs model inference and gets result.**
Model.Outputs outputs = model.process(image);
List<Category> probability = outputs.getProbabilityAsCategoryList();
String data = getHighestProbability(probability);
long time_elapsed = System.currentTimeMillis();
   
   

Releases the trained model resources if it is no longer used.
// Releases model resources if no longer used.
model.close();
Log.d("data_response", data);
   


Here I use the linear search algorithm to calculate the highest 
Probability with that algorithm, which means we find it will be in floating decimal points or it will be in a string type.
 String getHighestProbability(List<Category> probability) { // calculating the highest probability with linear search algorithm.
   float max0 = probability.get(0).getScore();
   String max1 = probability.get(0).getLabel();
   
   

Then we override the process and get a result from the 
Camera and send it to recognition.
Using try and catch the exception.

{
   Toast.makeText(this, "Failed to load", Toast.LENGTH_SHORT)
           .show();
   Log.e("Camera", e.toString());
}
   
   

Here I find the current battery level status while processing the multiple images for recognition in one go.
{ // getting current battery status.
   int level = intent.getIntExtra(BatteryManager.EXTRA_LEVEL, -1);
   int scale = intent.getIntExtra(BatteryManager.EXTRA_SCALE, -1);
   battery = (float) (level * 100 / scale);
}
   
   
   

Here I saving all the file with array data as txt formate using try and catch io exception.
This means when I will take multiple images from file explorer and send them to the adapter to recognise all the selected images then it will execute first all the images according to their time elapsed and then converting into the .txt file.

   
   
try {
       String receiveString = "bird_recognised,time_elapsed,battery_level \n";
       for (int i = 0; i < birdRecognised.length; i++) {
           receiveString = receiveString + birdRecognised[i] + ","+ timeElapsed[i]+","+batteryLevel[i]+"\n";

       }
                                                 
                                                 
                                                 
       OutputStreamWriter outputStreamWriter = new OutputStreamWriter(context.openFileOutput("csvfile" + System.currentTimeMillis() + ".csv", Context.MODE_PRIVATE));
       outputStreamWriter.write(receiveString);
       outputStreamWriter.close();
       Log.d("test1","rich");

   } 
        
                                                 
                                                 
                                                 
                                                 catch (IOException e) {
       Log.e("Exception", "File write failed: " + e.toString());
   }
}

                                                 

After arranging all the images according to their time elapsed then it will show a data to be printed in txt file.

final View DialogView = factory.inflate(R.layout.file_opner, null);
final AlertDialog DialogViewDialog = new AlertDialog.Builder(context).create();

## OUTPUT and RESULT

![WhatsApp Image 2022-12-17 at 1 59 06 AM](https://user-images.githubusercontent.com/85448730/208184333-8e6249f8-fddd-46fc-b596-6a2f9afd37a4.jpeg)
                                                                                  
![WhatsApp Image 2022-12-17 at 1 59 07 AM (1)](https://user-images.githubusercontent.com/85448730/208184351-8df9effb-8e12-41a8-96f8-aeac27276fe2.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 08 AM](https://user-images.githubusercontent.com/85448730/208184361-611e6e98-f7c6-4192-a0d2-cc88a6b248a3.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 06 AM (1)](https://user-images.githubusercontent.com/85448730/208184367-aef4319b-970f-4fab-8d0e-4fe7cbaf8938.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 08 AM (1)](https://user-images.githubusercontent.com/85448730/208184368-cca05765-4566-4767-b989-667096ea2331.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 09 AM (1)](https://user-images.githubusercontent.com/85448730/208184372-3bb5ca66-f7b1-4577-9bde-e8d5b1feaf15.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 09 AM](https://user-images.githubusercontent.com/85448730/208184377-01f7d1c5-6fc8-4171-963b-37807f30452a.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 10 AM](https://user-images.githubusercontent.com/85448730/208184379-25a1fd40-b998-4a63-aba2-5bfd8743ca6b.jpeg)
                                                 
![WhatsApp Image 2022-12-17 at 1 59 11 AM](https://user-images.githubusercontent.com/85448730/208184382-ceccde1f-70d2-4eb8-9a62-e9d24ef0b4d6.jpeg)


## RESULT
![MicrosoftTeams-image](https://user-images.githubusercontent.com/85448730/208234727-027b3bf6-f56b-47f1-9ae7-83a4b25c540e.png)


