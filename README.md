# DIPProject GAN

cd into the Docker folder and issue this command to build a docker image:

`docker build -t DIPgan_cuda -f Dockerfile_cubert_cuda .`

Once the image is built, reopen the code in a container

Download the cracked dataset folder from https://drive.google.com/drive/folders/1xIYX-pZXMsdCBwvl9qrF2Wo5dt5iXrpE?usp=drive_link
Download the uncracked dataset folder from https://drive.google.com/drive/folders/1vH7s3Tmo09A_BU6RX0zROmch858U3px_?usp=drive_link

Move both of these directories into DIPProject 

DIPProject/datasets/ is composed of training datasets with subdirectories of TrainA, TrainB, TestA, and TestB. The code will know which folders to access based on this organization. DIPProject/output consists of results from each dataset. Checkpoints are models that are labeled epoch_(epoch number) where epoch number is how many epochs the model has been trained for. Model progress is saved at the end of each epoch. The models are sampled every 100 iterations during training, and their output is shown in DIPProject/output/(dataset name)/samples_training. For testing, each image in testA will be uncracked, and they will be output in DIPProject/output/(dataset name)/samples_testing.


To run training, cd into DIPProject and enter this command

`python gan-models-torch/train.py --dataroot (dataset name) --model maskshadow_gan`

if your training stopped randomly, enter this command (let's say it stopped at epoch 94)

`python gan-models-torch/train.py --dataroot (dataset name) --model maskshadow_gan --restore --epoch_count 94`

To test a model at a certain epoch checkpoint (say epoch 134), cd into DIPProject and enter this command.

`python gan-models-torch/test.py --dataroot (dataset name) --model maskshadow_gan --epoch_count 134`


