# BIRD-Classifier-App

This Repository Contains the Projects Developed in Andriod(java).
The primary purpose of this project is to convert a tensor flow model into a tensor flow lite model and run it into the mobile application.
so here I will take a tensor flow model from [the tensor flow hub platform] then convert it into a tf life model and download a model.tflite and import it into the android studio.

Android Studio version: Dolphin|2021.3.1;

Flow chart of the app

![Unknown](https://user-images.githubusercontent.com/85448730/208182382-7f77a356-25cc-4fe2-b03c-2310ffccdb37.png)

First I initialised the package name.
(package com.mohit.birdsclassification;) 

Second, I import the essential libraries Import libraries - It can include everything needed to build an app, including source code, resource files, and an Android manifest  like;
import androidx.activity.result.ActivityResultLauncher;
import androidx.activity.result.contract.ActivityResultContracts;
import androidx.appcompat.app.AppCompatActivity;
import androidx.core.app.ActivityCompat;
import androidx.core.content.ContextCompat;

import com.mohit.birdsclassification.adapters.ProcessedImageAdapter;
import com.mohit.birdsclassification.databinding.ActivityMainBinding;
import com.mohit.birdsclassification.ml.Model;
import com.mohit.birdsclassification.utils.ViewAnimation;


Third I import the tf lite library to support the (Tensor image & label category)
import org.tensorflow.lite.support.image.TensorImage;
import org.tensorflow.lite.support.label.Category;


Here I define Activity binding to use for activity view binding it generates a binding class for each XML layout file in that module. An instance of a critical class contains direct references to all views with an ID in the corresponding layout.

![Picture 1](https://user-images.githubusercontent.com/85448730/208182882-64c4163d-66e5-4f86-b3dd-909a7e6aac51.png)

Broadcast Receivers can send or receive messages from other applications or from the system itself. These messages can be events or intents.


![Picture 2](https://user-images.githubusercontent.com/85448730/208183134-b01b32c7-b861-4b16-b10b-9508af5467ea.png)
