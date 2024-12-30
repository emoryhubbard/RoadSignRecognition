# Convolutional Neural Network for Road Sign Recognition

This CNN is an image classifer I created and fine-tuned for recognizing German road signs, for usage by a hypothetical self-driving car, and which achieved 92% accuracy. I experimented with several different architectures, including Xception-based models.

The exact classification task is to identify one of 43 different types of German road signs based on an image input.

Five different variations of road sign recognition models were developed in order to try as many approaches as feasible. A much higher performance is achievable, when any of these models is compared to performance of other state-of-the-art models for similar problems, and with more time to experiment and fine-tune, it is clear those performances can be matched based on the rate of improvement below.

Source code for initializing and training the final model appears in [roadsign_32x32model.ipynb](https://github.com/emoryhubbard/RoadSignRecognition/blob/main/roadsign_32x32model.ipynb)


## Xception and Custom Model Comparisons

### I. Xception-based 71x71 Model Results
The Xception-based 71x71 Model created for road sign recognition demonstrated that it was possible to incorporate an existing, pre-trained CNN architecture to use on this problem, and achieve functional image classification, ie. transfer learning. It also demonstrated data augmentation being performed in a separate layer, integrated into the model.
The training accuracy was 71%, and the validation accuracy was 49%, which is in need of much improvement.
However, this model was capable of being trained within several minutes, making it practical as a proof-of-concept test before larger, more ambitious models were trained.

### II. Xception-based 150x150 Model Results
The small input image size of 71x71 enabled the Xception-based 71x71 Model to be trained faster, but it was suspected that this might be impacting the performance negatively. To test this hypothesis and improve performance, the images were resized to use 150x150 pixels for this model.
The results yield an increase in validation accuracy from 49% to approximately 62%, and it took approximately 4 hours of training time.
There is a final fine-tuning process that can be applied to increase model performance further, perhaps as much as 2% or 5%, with both this and the previous model, but due to the low final validation accuracy, efforts instead turned to alternative architectures.

### III. Custom 100x100 Architecture Results
A model with the following shape was constructed for this problem:

![Custom 100 x 100 Shape image](Custom100x100Shape.png)

Compared to the previous model, the validation accuracy increased from 62% to 88%.

However, in the process of creating this model, there was a bit of serendipity, as an earlier test model actually achieved higher accuracy, which will be described next.

###IV. Custom 32x32 Architecture Results
It was unexpected that a 32x32 image resizing would perform better than the model taking 100x100 images. It was only intended as a brief test before training the larger model.

However, the results were better than all previous attempts:

![Custom 32 x 32 Partial Holdout image](Custom32x32Validation.png)

This is a validation accuracy of 92%, improving upon the 88% previously described.

To confirm this validation accuracy, the next step was testing the model against a partial hold-out set, which revealed the following accuracy report. Since the accuracy number in this report is similar, this indicates that the model is performing as intended.

![Alt text](Custom32x32PartialHoldout.png)

Reminder: source code for initializing and training the final model appears in [roadsign_32x32model.ipynb](https://github.com/emoryhubbard/RoadSignRecognition/blob/main/roadsign_32x32model.ipynb)
