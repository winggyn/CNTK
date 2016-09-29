# CIFAR-10 Dataset

The CIFAR-10 dataset (http://www.cs.toronto.edu/~kriz/cifar.html) is a popular dataset for image classification, collected by Alex Krizhevsky, Vinod Nair, and Geoffrey Hinton. It is a labeled subset of the [80 million tiny images](http://people.csail.mit.edu/torralba/tinyimages/) dataset.

The CIFAR-10 dataset consists of 60,000 32x32 color images in 10 classes, with 6,000 images per class. There are 50,000 training images and 10,000 test images. The 10 classes are: airplane, automobile, bird, cat, deer, dog, frog, horse, ship, and truck. 

The CIFAR-10 dataset is not included in the CNTK distribution but can be easily downloaded and converted to CNTK-supported format by running the following Python command:

```
python CifarDownload.py [-f <format: cudnn|legacy>]
```
The download script has an optional `-f` parameter which specifies output format of the datasets. `cudnn` option (default) saves dataset in a spatial-major format used by cuDNN, while `legacy` option saves in CNTK legacy format. Use `cudnn` if CNTK is compiled with cuDNN and `legacy` otherwise. We strongly recommend the users to use the default `cudnn` option.

After running `CifarDownload.py`, you will see the original CIFAR-10 data are copied in a folder named `cifar-10-batches-py`. Meanwhile, two text files `Train_cntk_text.txt` and `Test_cntk_text.txt` are created in the current folder. These text files can be read directly by CNTK.

If you are interested in experimenting with CNTK's `ImageReader`, you shall further convert the CIFAR-10 dataset with the following command:

```
python CifarConverter.py <path to CIFAR-10 dataset>
```

Here `<path to CIFAR-10 dataset>` can be simply `cifar-10-batches-py`. The script will create a `train` and a `test` folder that store train and test images in png format. It will also create appropriate mapping files (`train_map.txt` and `test_map.txt`) for the CNTK `ImageReader` as well as mean file `CIFAR10_mean.xml`.

We provide multiple examples in the [Classification](../../Classification) folder to train classifiers for CIFAR-10 with CNTK. Please refer there for more details.

If you are curious about how well computers can perform on CIFAR-10 today, Rodrigo Benenson maintains a [blog](http://rodrigob.github.io/are_we_there_yet/build/classification_datasets_results.html#43494641522d3130) on the state-of-the-art performance of various algorithms.