# Real-time-Face-Mask-Detection
The code is for training a mask detection model using both a custom CNN and MobileNetV2.

 **Preprocessing**:
   - Load and preprocess images from the dataset directory.
   - Perform one-hot encoding on the labels.

Custom CNN:
1. **Custom CNN Model**:
   - Define a custom CNN model with Convolutional, MaxPooling, Flatten, Dense, and Dropout layers.
   - The final layer has two output units and uses the softmax activation function to predict whether an image contains a mask or not.
   - The model is compiled using the Adam optimizer with a learning rate of 0.001 and categorical cross-entropy as the loss function.
     
2. **Training the Custom CNN Model**:
   - It is trained using the training data (trainX and trainY) with a batch size of 100 and 20 epochs , achieving 97% accuracy
   - A validation split of 20% is used for validation during training.
     
3. **Evaluation of the Custom CNN Model**:
   - Evaluate the performance of the custom CNN model on the test data.
   - The classification_report function from sklearn is used to display a formatted classification report, including metrics like precision,
      recall, and F1-score.

4. **Saving the Custom CNN Model**:
   - The trained custom CNN model is saved to disk in the "mask_detector2.model" file using the h5 format.

MobileNetV2:
1. **Training MobileNetV2 with Custom Head**:
   - Set up data augmentation using ImageDataGenerator.
   - Load MobileNetV2 with pre-trained ImageNet weights, excluding the top layers.
   - Construct a custom head model on top of MobileNetV2.
   - Combine the head model with MobileNetV2 to create the final model.
   - Freeze the base layers of MobileNetV2.

2. **Training the MobileNetV2 with Custom Head**:
   - The model is compiled using the Adam optimizer .
   - The head of the network is trained using the augmented training data from aug.flow, achieving 98% accuracy

3. **Evaluation of the MobileNetV2 with Custom Head**:
   - Evaluate the performance of the MobileNetV2 with the custom head model on the test data.

4. **Saving the MobileNetV2 with Custom Head Model**:
   - The trained MobileNetV2 with the custom head is saved to disk in the "mask_detector.model" file using the h5 format.
  
Real mask detection :
 - It loads the face detection model and the trained mask detection model. 
 - The code then captures video frames from the webcam, detects faces using the face detection model, 
    and classifies each face as wearing a mask or not using the mask detection model.
 - The results are displayed on the output frame in real-time.
 - The program can be terminated by pressing the 'q' key.
