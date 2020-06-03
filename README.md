# Brain_Tumour_Detection
Using Pre-processing and CNN to detect Brain Tumour from MRI Images


Data Augmentation-
The dataset consists of two folders i.e. Yes and No containing 253 Brain MRI Images. The
folder Yes consists of 155 Brain MRI Images which have tumour and folder No consists of
98 Brain MRI Images that does not have tumour.
Since I have used the less dataset that’s why Data Augmentation is used in this project so that
more images are created. It is done so that data is balanced from both the sides.


Data Preparation & Pre-processing-
In order to focus on the Tumour part of the Brain MRI Image more clearly the images are
cropped from top, bottom, right, left. The Brain parts are cropped from the images.
The image also undergoes through gray scaling and blurring of the image and then
morphological operations like Dilation and Erosion are performed to remove any kind of
noise present in the image.
Then from the threshold image largest contour is selected to find the extreme points so that
we can crop out a new image that focuses clearly on the Brain part of the image.


Reading of the Data- 
This following function takes 2 arguments into account, the first one being the list of
directory paths containing the folders Yes and No that further contains the image data and the
second argument being resizing of the image.
Following steps are performed:
1. Reading of the image.
2. Cropping the part of the image that represents only the brain.
3. Resizing of the image since all the images comes in different sizes. So fixing the
size of the image to be (240, 240, 3) for training of our data.
4. Normalizing the images as we want the pixel values to be scaled to the range of
0-1.
5. Now the image is appended to X and its label is appended to y.
6. Since the data is now in ordered manner so we now shuffle the arrays X and y.


Plotting of the Images-
Now the various datasets i.e. Yes and No containing Brain MRI Images are then plotted
showing the images in Yes containing images having tumour and No containing images not
having tumour.


Splitting of the Data-
Now the dataset is splitted for training, validation and testing
Splitting is done in following manner:
1. 70% of the data for training
2. 15% of the data for validation
3. 15% of the data for testing


Building the Model and Training -
Now the Neural Network model is built.
While building of the model first Zero Padding is done using ZeroPadding2D function, and
then a Convolutional kernel is created by Conv2D function and then maximum element is
selected from the region by MaxPooling2D function and then finally using Flatten function
the output of the above procedure is converted to a single vector.
After performing all these functions we redefine the shape of the image to the previous size
of the image i.e. (240, 240, 3).
After building the model finally the data is trained.
Understanding the architecture:
Each input x (image) has a shape of (240, 240, 3) and it is fed into the neural network.
So, it goes through the following layers:
1. A layer of Zero Padding with a pool size of (2, 2).
2. A convolutional layer with 32 filters, having a filter size of (7, 7) and a stride equal to 1
3. A batch normalization layer to normalize the pixel values to speed up computation.
4. A ReLU activation layer.
5. A Max Pooling layer with f=4 and s=4.
6. A Max Pooling layer with f=4 and s=4, same as before.
17BEC0548 – Kartik Gupta
7. A flatten layer in order to flatten the 3-dimensional matrix into a one-dimensional
vector.
8. A Dense (output unit) fully connected layer with one neuron with a sigmoid activation
(since this is a binary classification task).


Plotting Loss and Accuracy-
Now after training is done we go for plotting of accuracy of the data that how much data is
accurate to results from the dataset containing tumoured images and also plotting of Loss of
the data is done so that we can get the idea of training the data to get accurate result.
