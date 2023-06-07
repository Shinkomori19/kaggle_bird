# kaggle_bird

## Group members
* Shin Komori
* Tatsuhiko Araki

## Problem description
* We joined the bird Kaggle competition.
  * The problem was to identify which bard is in given pictures from more than 500 species.  
* Other than submitting to Kaggle competition, we explored various learning techniques that we were interested in. We tried 
  * Auto-tuning of learning rate
  * Fine tuning of pre-trained models
  * Ensemble learning

## Previous work
* We used pretrained models, such as;
  * ResNet 18
  * ResNet 50
  * VGG 19
  * Efficient Net
* Also, we used PyTorch to keep our code simple. 
  * Especially, optimizer and loss functions were useful
* We implemented codes to train, evaluate, and to ensemble prediction.

## Dataset
* We used the given dataset of bird
* We split train data into train data and validation data, so that we can evaluate our model by using validation data.
* Pre-trained models used ImageNet for pre-training.

## Problems we encountered
* Training took much more time than we expected.
  * We were not able to do brute force hyper parameter search or try all possible models because of the limitation of time and computational resources.
* Using Kaggle was difficult because it was our first time.
  * We did not know how to use notebooks, how to submit results.
* When we defined models ourselves, it did not achieve good performance, and we gave up defining models ourselves. Pre-trained models achieved better results, which was impressive but we wanted to do better by not using off-the-shelf methods.

## What we did
1. Submitted to Kaggle competition.
2. Explored various learning techniques that we were interested in. We tried
    1. Auto-tuning of learning rate
    2. Fine tuning of pre-trained models
    3. Ensemble learning
##### About Kaggle competition
* We used ResNet 50, since it has more parameters than ResNet 18, which means it is more expressive. 
* We did data augmentation to make the training effective.
* We achieved 70% or accuracy, by simply using ResNet 50 architecture.

##### Auto-tuning of learning rate
<img width="500" alt="スクリーンショット 2023-06-06 224914" src="https://github.com/Shinkomori19/kaggle_bird/assets/104906428/fa6641b4-60c1-4764-975b-02d495908bb2">

* Since this typical graph of loss value when changing the learning rate looks inefficient, we tried to make the curve smooth. We tried three patterns.
    1. Check the loss value for each iteration and update the learning rate if the value increases. This caused so many updates, and the training became very slow. The condition for updating the learning rate was too easy to meet.
    2. Check the sum of the loss for every 10 iterations and update the learning rate if the value increases.
    3. Check the sum of the loss value for each epoch and update the learning rate if the value increases. This did not cause much update, so the condition was too strict.

##### Ensemble Learning with ResNet18 + VGG19
* We defined Decision Tree based architecture by ourselves using scikit-learn and CNN based architecture, but they did not achieve good performance at all, so we shifted to pre-trained models. Each performance was about 2-4% accuracy on a small test set that we prepared

<img width="500" alt="スクリーンショット 2023-06-06 225632" src="https://github.com/Shinkomori19/kaggle_bird/assets/104906428/1d62b801-768d-4290-8208-bc66c3066c84">

* We tried a technique called “ensemble learning”, where we train independent models and combine them to achieve better performance.
   1. Single ResNet18 
     * When trained, it achieved a loss of 1.87 and accuracy of 51%<img width="500" alt="スクリーンショット 2023-06-06 230030" src="https://github.com/Shinkomori19/kaggle_bird/assets/104906428/39216fb9-b563-4275-a73f-75b03f5a4e2b">
     
   2. Single VGG19 
     * When trained, it achieved a loss of 3.57 and accuracy of 24%
     <img width="500" alt="スクリーンショット 2023-06-06 230151" src="https://github.com/Shinkomori19/kaggle_bird/assets/104906428/08adcba4-7d4b-4954-863f-0154d1715cf4">
     
   3. Combined model
     * We combined the two to conduct ensemble analysis. By taking a weighted sum of each predicted probabilities, we predicted the final result as one model. Formula of `argmax(a*(resnet_probabilities) + (1-a)*(vgg_probabilities))` was used. As a result of hyper parameter search of a, we gained 
     
<img width="500" alt="スクリーンショット 2023-06-06 230859" src="https://github.com/Shinkomori19/kaggle_bird/assets/104906428/cbdabb73-fda1-4fa4-98a0-dcf6743595b1">

## Problems we encountered
* We used ResNet 50, since it has more parameters than ResNet 18, which means it is more expressive.
* We did data augmentation

## Next step
* About auto tuning of learning rate, we can try various patterns to search when is the best time to update the learning rate
  * How do we scale it when updating? (e.g. ½, ⅓, ¼ ?)
  * What should be the condition for updating?
* Improve the accuracy of each model
  * Further hyper parameter tuning can be done, with more time and computational resources.
  * We used one model per algorithm (CNN, Decision Tree). Based on the same algorithms, there are multiple possible structures of the models like the number of layers of CNN layers, etc. We can get higher accuracy by exploring those different architectures, even if we use the same algorithm.
* Increase the number of models that we use.
  * We used two models this time, but we can expect higher accuracy by combining more than two different models based on different algorithms.
  * We might be able to get better results by having multiple models based on the same or similar architectures too.
* Reduce the amount of time it takes to train
  * Think about how many digits we need to train
  * Use Attention-based mechanisms

## Code
https://colab.research.google.com/drive/1KHlZ_S0lL9XDLcTHX6VfPyCHia87I6US?usp=sharing

