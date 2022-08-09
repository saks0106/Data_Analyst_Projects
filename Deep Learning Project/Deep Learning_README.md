
# Food Multiclass Classification Project

![](https://media.istockphoto.com/photos/bbq-feast-picture-id694177316)


Sago Coffee House @ New York (same as our Data Visualization Project) has gained tremendous Success in the last few years and has decided to venture even further by adding various cuisine to their existing Menu and giving Customer a great variety of Food Dishes from all over the world. 

**The Project**: Sago wants to enhance Customer Experience even further. The task is simple:
When the Customer enters the restaurant, they are introduced to many food dishes & in most cases they would be unaware of it but willing to try the dish. Sago's CEO wants a mobile application wherein when the User clicks the photo of the food dish, the application tells which dish it is & all the necessary information along with it to make the Customer try it once.

Sam the inhouse Data Scientist & Deep Learning Expert is called upon for this task. His task is to gather all the images of different food items, prepare and train Deep Learning Models based on varying images of food items having different quantities and qualities.

## Food Multiclass Classification Book 1: Knowing the Data & Binary Class Food Classification
Book 1 contains the prerequisites to prepare the final high accuracy model. Here we are introducted to Tensorflow with Keras. 

We understand steps of Modelling like:

    1.Creating a model
    2.Compiling the model 
    3.Fitting the model. 

We almost everytime tweak these 3 steps to achieve better accuracy then the previous models.

For hands on purposes, we first try to create a model for make_circles dataset available on **Tensorflow** using Keras to differentiate between inner to outer scatter plot cirlces that is **Binary Classification**. We then jump to **Multiclass Classification** using  `tf.keras.datasets` for loading Fashion MNist Dataset.

We then start with **Convolutional Neural Network & Computer Vision**. Our real Food Vision Project starts here. We start small by dealing with just 2 food images dataset of 1000 images of Pizza and Steak. We first try with normal images and then try to augment the images so that model learns different patterns in the image.

After trying couple of hand made model using Sequential **Conv2D** & **MaxPool2D** and tuning their hyperparameters, we still struggle to get a decent Accuracy score. Let's try some more advance methods in Book 2 and Book 3.


 - [Deep Learning Book 1](https://github.com/saks0106/Data_Science_Projects/blob/master/Deep%20Learning%20Project/1_Food_Vision_101_Part1_Knowing_the_data.ipynb)



## Food Multiclass Classification Book 2: Mini Food Multiclass Classification with Transfer Learning
We take the 2 class from Book 1 that is Pizza and Steak along with 8 other Food Classes which now contains 7500 images (each class has 750 images). Using our previously build models in Book 1 for our current 10 classes Food Classification gives a meagre  ~35% to ~40% accuracy which is not practical. So we try **Transfer Learning**.

Transfer learning: **Feature Extraction** taking the patterns (weights) another model has learned from another problem and using them for our own problem. What this means is, instead of hand-crafting our own neural network architectures or building them from scratch, we can utilise models which have worked for others for similar kind of Dataset. **TensorFlow Hub** is a repository for existing model components. It makes it so we can import and use a fully trained model with as little as a URL.

For our Food Classification, we use 2 TensorFlow Hub Models- ResNetV250 & EfficientNetB0. 

Next we try another type of Transfer Learning: **Fine-Tuning**. In fine-tuning transfer learning the pre-trained model weights from another model are unfrozen and tweaked during to better suit our own data and use Functional API instead of Sequential API. 

After tweaking and playing with different models, we try to predict the food class with just 1% of Data that is just 7 images in every training class and 250 images for test data and gradually increasing the training dataset to check the model Accuracy.

We also combine Fine Tuning Transfer Learning to open up top 10 frozen layers so that model learns and updates it's weights based on our data. Finally we end the Book through our final model where in all the 7500 dataset with Data Augmentation and Fine Tuning Transfer Learning to predict the model Accuracy and Finally compare different models on **TensorBoard**.

 - [Deep Learning Book 2](https://github.com/saks0106/Data_Science_Projects/blob/master/Deep%20Learning%20Project/2_Food_Vision_101_Part2_Gearing_up_Mini_Food_Vision_With_GPU.ipynb)

## Food Multiclass Classification Book 3:  Scaling up the project Full Dataset

After dealing with binary classification & then 10 food multiclass classification, it's time we take this project to the finish line by taking all 101 food images dataset together & train our model. 

There are 1000 images per class (750 of each class in the training set and 250 of each class in the test set), totalling 101,000 imags but let's keep it for the final high accuracy model. For now we'll deal with 101 food classes we'll be building a model on 75 training images and evaluating it on 250 test images. We'll also start by using feature extraction transfer learning with a pre-trained model for a few epochs and then fine-tune for a few more epochs using EfficientNetB0.

After getting our desired model, we make predictions, evaluate our model's predictions using `sklearn.metrics` to import **Confusion Matrix** & see were our model is getting Confused. We also import **classification_report** to know the `precision`,`recall`,`f1`,`support`.

With the help of bar graph, we need to understand which food classes have highest **F1** score as its the combination of precision and recall. After tweaking the hyperparameters, it's time to predict the food classes on our test and custom images.

We then find why our model is predicting some images with a very high prediction probability, meaning it's very confident with its prediction but still getting the label wrong. These most wrong predictions can help to give further insight into our model's performance ie close to 1 predicting but wrong prediction. Other case could be the original image itself has wrong label but model predicted it right!

Finally after working on small & medium size dataset,it's time we bring in our mammoth dataset of 101,000 images. Before we load the dataset, We're going to use two methods to significantly improve the speed of our model training:

    1.Prefetching & multithreaded loading & processing- images are loading in the Cache Memory & our Batch size images are loaded in GPU simultaneously
    2.Mixed precision training - uses a combination of single precision (float32) and half-preicison (float16) data types to speed up model training (up 3x on modern GPUs).


We then train our model on similar lines as used earlier using Data Augmentation, Transfer Learning Fine Tuning using Prefetching & Mixed precision, loading via Functional API and then fit the model and carry out hyperparameters tweaking if needed.

We come to the last state of saving the model and loading the saved model to check if everything works as expected. Our Food Vision Model is ready to be handed to the Development team who will bring our model alive and finally complete the company's Requirements.

 - [Deep Learning Book 3](https://github.com/saks0106/Data_Science_Projects/blob/master/Deep%20Learning%20Project/3_Food_Vision_Part3_Scaling_up_%26_Final_With_Full_101_Dataset.ipynb)

Sago's CEO is very happy as Sales have now increased tremendously as Customers try different food dishes which they were unaware of before.


## Feedback & Queries

If you have any feedback or Queries, please reach out to me at sakshemgotekar@gmail.com






