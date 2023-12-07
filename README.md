# DIPProject GAN

cd into the Docker folder and issue this command to build a docker image:

`docker build -t DIPgan_cuda -f Dockerfile_cubert_cuda .`

Once the image is built, reopen the code in a container

Move both of these directories into DIPProject 

DIPProject/datasets/ is composed of training datasets (such as shadow_USR) with subdirectories of TrainA, TrainB, TestA, and TestB. The code will know which folders to access based on this organization. DIPProject/output consists of results from each dataset. Checkpoints are models that are labeled epoch_(epoch number) where epoch number is how many epochs the model has been trained for. Model progress is saved at the end of each epoch. The models are sampled every 100 iterations during training, and their output is shown in HyperGAN/output/shadow_USR/samples_training. For testing, each image in testA will be deshadowed, and they will be output in DIPProject/output/shadow_USR/samples_testing.


To run training, cd into DIPProject and enter this command

`python gan-models-torch/train.py --dataroot shadow_USR --model maskshadow_gan`

if your training stopped randomly, enter this command (let's say it stopped at epoch 94)

`python gan-models-torch/train.py --dataroot shadow_USR --model maskshadow_gan --restore --epoch_count 94`

To test a model at a certain epoch checkpoint (say epoch 134), cd into HyperGAN and enter this command.

`python gan-models-torch/test.py --dataroot shadow_USR --model maskshadow_gan --epoch_count 134`


