# kaggle_bird

# Problem description
* We joined the bird Kaggle competition.
  * The problem was to identify which bard is in given pictures from more than 500 species.  
* Other than submitting to Kaggle competition, we explored various learning techniques that we were interested in. We tried 
  * Auto-tuning of learning rate
  * Fine tuning of pre-trained models
  * Ensemble learning

# Previous work
* We used pretrained models, such as;
  * ResNet 18
  * ResNet 50
  * VGG 19
  * Efficient Net
* Also, we used PyTorch to keep our code simple. 
  * Especially, optimizer and loss functions were useful
* We implemented codes to train, evaluate, and to ensemble prediction.

# Dataset
* We used the given dataset of bird
* Pre-trained models used ImageNet for pre-training.

# Problems we encountered
* Training took much more time than we expected.
  * We were not able to do brute force hyper parameter search or try all possible models because of the limitation of time and computational resources.
* Using Kaggle was difficult because it was our first time.
  * We did not know how to use notebooks, how to submit results.
* When we defined models ourselves, it did not achieve good performance, and we gave up defining models ourselves. Pre-trained models achieved better results, which was impressive but we wanted to do better by not using off-the-shelf methods.

# What we did
1. Submitted to Kaggle competition.
2. Explored various learning techniques that we were interested in. We tried
    1. Auto-tuning of learning rate
    2. Fine tuning of pre-trained models
    3. Ensemble learning

# Problems we encountered
* We used ResNet 50, since it has more parameters than ResNet 18, which means it is more expressive.
* We did data augmentation


- epoc ごとに評価して、その値が悪くなったときのみ lr を下げるというテクニックがよく使われる。
- PyTorch のチュートリアルに、ResNet からのファインチューニングを birds のデータに適用するコードあり
- Google Drive 上に学習データを持っておくとよいかも



Submit the url to your project website. The website should have your project video as well as the content described in the Ed post (as applicable):

Problem description
Previous work (including what you used for your method i.e. pretrained models)
Your approach
Datasets
Results
Discussion
What problems did you encounter?
Are there next steps you would take if you kept working on the project?
How does your approach differ from others? Was that beneficial?



以下Edのコピペ
Explore any aspect of CV that interests you

Should probably include substantial coding of your own but I encourage you to also use outside libraries/frameworks (pytorch, tensorflow, opencv, etc.)

Should be roughly equivalent in work to 2 homework in technical work/scope

Deliverable: Your final project presentation will be a website describing your project, and a 2-3 minute video. This summary should mention the problem setup, data used, techniques, etc. It should include a description of which components were from preexisting work (i.e. code from github) and which components were implemented for the project (i.e. new code, gathered dataset, etc).

