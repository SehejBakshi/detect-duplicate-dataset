# Detect and remove duplicate images from a dataset
This Python program checks an image dataset for duplicate images and removes them.

## Why is it necessary?
Having duplicate images in your dataset creates a problem for two reasons:

1. It <strong>introduces bias</strong> into your dataset, giving your deep neural network additional opportunities to learn patterns specific to the duplicates
2. It hurts the ability of your model to generalize to new images outside of what it was trained on

While we often assume that data points in a dataset are independent and identically distributed, that’s rarely (if ever) the case when working with a real-world dataset. When training a Convolutional Neural Network, we typically want to remove those duplicate images before training the model.

Secondly, trying to manually detect duplicate images in a dataset is extremely time-consuming and error-prone — it also doesn’t scale to large image datasets. We therefore need a method to automatically detect and remove duplicate images from our deep learning dataset.

We’ll implement our image duplicate detector using a method called <strong>image hashing.</strong>

## Process
To detect and remove duplicate images from a dataset, I created a “practice” dataset we can use based on the <a href="http://vision.stanford.edu/aditya86/ImageNetDogs/">Stanford Dogs Dataset.</a>

This dataset consists of 20,580 images of dog breeds, including Beagles, Newfoundlands, and Pomeranians, just to name a few.

To create the duplicate image dataset, I:

1. Downloaded the Stanford Dogs Dataset
2. Sampled three images that I would duplicate
3. Duplicated each of these three images a total of N times
4. Then randomly sampled the Stanford Dogs Dataset further until I obtained <strong>1,000</strong> total images

![Duplicates in the dataset.](images/duplicate_counts.jpg?raw=true "Duplicates in the dataset.")

## Running our image duplicate detector
Let’s put our image duplicate detector to work.

Let's check our dataset size before running this program!

![Before deleting duplicate images](images/before.jpg?raw=true "Before deleting duplicate images")

So there are a 1000 images in the dataset before detecting and deleting the duplicate images.

To run this program, open your terminal/cmd in the same directory and type: <strong>python detect_and_remove.py --dataset dataset</strong>
  
This will show you the images that are duplicates and their correspoding hash values.

![Duplicate 1](images/montage1.jpg?raw=true "Duplicate 1")

![Duplicate 2](images/montage2.jpg?raw=true "Duplicate 2")

![Duplicate 3](images/montage3.png?raw=true "Duplicate 3")


Now that our duplicate images have been identified, let's remove them from the dataset. To actually remove the duplicates from our system, we need to execute detect_and_remove.py again, this time supplying the --remove 1 command line argument.

To do this, type in the following command on your terminal/cmd: <strong>python detect_and_remove.py --dataset dataset --remove 1</strong>

Let's check our dataset size now.

![After deleting duplicate images](images/after.jpg?raw=true "After deleting duplicate images")

Originally, there were 1000 images in dataset, but now there are 993, implying that we removed the 7 duplicate images. So it seems that we have deleted all the duplicate images from our dataset!
