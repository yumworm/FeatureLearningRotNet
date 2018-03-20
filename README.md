## *Unsupervised Representation Learning by Predicting Image Rotations*

### Introduction

The current code implements on [pytorch](http://pytorch.org/) the following ICLR2018 paper:    
**Title:**      "Unsupervised Representation Learning by Predicting Image Rotations"    
**Authors:**     Spyros Gidaris, Praveer Singh, Nikos Komodakis    
**Institution:** Universite Paris Est, Ecole des Ponts ParisTech    
**Code:**        https://github.com/gidariss/FeatureLearningRotNet   
**Link:**        https://openreview.net/forum?id=S1v4N2l0-

**Abstract:**  
Over the last years, deep convolutional neural networks (ConvNets) have transformed the field of computer vision thanks to their  unparalleled capacity to learn high level semantic image features. However, in order to successfully learn those features, they usually require massive amounts of manually labeled data, which is both expensive and impractical to scale. Therefore, unsupervised semantic feature learning, i.e., learning without requiring manual annotation effort, is of crucial importance in order to successfully harvest the vast amount of visual data that are available today. In our work we propose to learn image features by training ConvNets to recognize the 2d rotation that is applied to the image that it gets as input.  We demonstrate both qualitatively and quantitatively that this apparently simple task actually provides a very powerful supervisory signal for semantic feature learning.  We exhaustively evaluate our method in various unsupervised feature learning benchmarks and we exhibit in all of them state-of-the-art performance. Specifically, our results on those benchmarks demonstrate dramatic improvements w.r.t. prior state-of-the-art approaches in unsupervised representation learning and thus significantly close the gap with supervised feature learning. For instance, in PASCAL VOC 2007 detection task our unsupervised pre-trained AlexNet model achieves the state-of-the-art (among unsupervised methods) mAP of 54.4%$that is only 2.4 points lower from the supervised case.  We get similarly striking results when we transfer our unsupervised learned features on various other tasks, such as ImageNet classification, PASCAL classification, PASCAL segmentation, and CIFAR-10 classification.

### Citing FeatureLearningRotNet

If you find the code useful in your research, please consider citing our ICLR2018 paper:
```
@inproceedings{
  gidaris2018unsupervised,
  title={Unsupervised Representation Learning by Predicting Image Rotations},
  author={Spyros Gidaris and Praveer Singh and Nikos Komodakis},
  booktitle={International Conference on Learning Representations},
  year={2018},
  url={https://openreview.net/forum?id=S1v4N2l0-},
}
```

### License
This code is released under the MIT License (refer to the LICENSE file for details). 

### Before running the experiments
* Inside the *FeatureLearningRotNet* directory with the downloaded code you must create a directory named *experiments* where the experiments-related data will be stored: `mkdir experiments`.
* You must download the desired datasets and set in [dataloader.py](https://github.com/gidariss/FeatureLearningRotNet/blob/master/dataloader.py#L21) the paths to where the datasets reside in your machine. We recommend creating a *datasets* directory `mkdir datasets` and placing the downloaded datasets there. 
* Note that all the experiment configuration files are placed in the [./config](https://github.com/gidariss/FeatureLearningRotNet/tree/master/config) directory.

### CIFAR-10 experiments
* In order to train (in an unsupervised way) the RotNet model on the CIFAR-10 training images and then evaluate object classifiers on top of the RotNet-based learned features see the [run_cifar10_based_unsupervised_experiments.sh](https://github.com/gidariss/FeatureLearningRotNet/blob/master/run_cifar10_based_unsupervised_experiments.sh) script.
* In order to run the semi-supervised experiments on CIFAR-10 see the [run_cifar10_semi_supervised_experiments.sh](https://github.com/gidariss/FeatureLearningRotNet/blob/master/run_cifar10_semi_supervised_experiments.sh) script.

### ImageNet and Places205 experiments
* In order to train (in an unsupervised way) a RotNet model with AlexNet-like architecture on the **ImageNet** training images and then evaluate object classifiers (for the ImageNet and Places205 classification tasks) on top of the RotNet-based learned features see the [run_imagenet_based_unsupervised_feature_experiments.sh](https://github.com/gidariss/FeatureLearningRotNet/blob/master/run_imagenet_based_unsupervised_feature_experiments.sh) script.
* In order to train (in an unsupervised way) a RotNet model with AlexNet-like architecture on the **Places205** training images and then evaluate object classifiers (for the ImageNet and Places205 classification tasks) on top of the RotNet-based learned features see the [run_places205_based_unsupervised_feature_experiments.sh](https://github.com/gidariss/FeatureLearningRotNet/blob/master/run_places205_based_unsupervised_feature_experiments.sh) scritp.


### Download the already trained RotNet model
* In order to download the RotNet model (with AlexNet architecture) trained on the ImageNet training images using the current code, go to: [ImageNet_RotNet_AlexNet_pytorch](https://mega.nz/#!n81AnC6L!xTbo_D3xd7QOpOSG1UFSChmDr8mbcuWbVjhQMaC4yoE). Note that:   
  1. The model is saved in pytorch format.   
  2. It is not the same as the one used in the paper and probably will give (slightly) different outcomes (in the ImageNet and Places205 classification tasks that it was tested it gave better results than the paper's model).    
  3. It expects RGB images that their pixel values are normalized with the following mean RGB values `mean_rgb = [0.485, 0.456, 0.406]` and std RGB values `std_rgb = [0.229, 0.224, 0.225]`. Prior to normalization the range of the image values must be [0.0, 1.0].
