#########################################################################################################################
***********************************************Course Information********************************************************

                            	     EEE 511: Artificial Neural Computation           
                                                Sem - Fall 2020                     
                                            Arizona State University                    
                                           Instructor: Dr. Jennie Si                 

*************************************************************************************************************************
#########################################################################################################################

#########################################################################################################################
--------------------------------------------------Final Project----------------------------------------------------------

Team No: 18

Author 1: Viraj Savaliya    ; ASU ID -1217678787
Author 2: Raunak            ; ASU ID -1217240245
Author 3: Nayankumar Patel  ; ASU ID -1217420191

Project Title: High Speed Ball Detection and Tracking

Attached Files:
1. Final Report(IEEE paper format) for project
2. Presentation ppt
3. Presentation video link
4. Github repository of the source code for model implemented
5. Credit report

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------Steps for Dataset preparation-------------------------------------------------


Prerequisites: MATLAB Runtime with MATLAB version 9.2 (R2017a)

1. Trim the original video of the entire match into mulitple clips where game is in play
2. Open LabelingTool.exe present under anc-project/tree/master/tracknet/labelingTool/LabelingTool/for_testing
3. In the tool window select open in top left corner and select a directory of video clip
   (Need to repeat this step for all clip directories)
4. Move the cursor and click on where the ball is located in the frame to mark x and y co-ordinates
5. Select approporiate features on the side bar for the frame
   Visibility : No ball / Easy Identification / Hard Identification / Occluded
   Status : Flying / Hit / Bouncing
6. Use right and left arrow key to switch frames and Repeat steps 4 and 5 for all frames in the directory.
   (Already marked frames will have the frame patch text above the image in blue or else in red if not labeled)
7. After all frames labeled, click output in the bottom right corner to generate 'Label.csv' file in the directory
   (This is the labeled csv dataset file for that clip. Each clip will have its own Label.csv)


-------------------------------------------------------------------------------------------------------------------------
--------------------------------------------Steps for Training the model-------------------------------------------------

Prerequisites: Google Colab, labeled dataset

1. Start Google Colab, select python 2.7 version, Select GPU and Select tensorflow 1.x.
2. Put the code in the Google Drive and load the code in the Google Colab by connecting it to the drive.
3. Go to code, open Tracknet_Python.ipynb file.
4. Make a new folder by the name of Groundtruth in the code folder. Put the dataset in that Groundtruth folder.
5. Specify the correct path in the first code specifying the correct location of the dataset.
6. Run the first code in Tracknet_python.ipynb to create groundtruth images.
7. Update the groundtruth path and the original dataset pth in the second code to create training and testing csv files.
8. Copy the training and testing files in the Tracknet_Three_Input folder.
9. Then use the following command to train the model,

 python train.py --save_weights_path=weights/model.3 --training_images_name="training_model3.csv" --epochs=500 
--n_classes=256 --input_height=360 --input_width=640 --load_weights=2 --step_per_epochs=200 --batch_size=2

10. Wait till training is finished. model.3 trained weights will be generated in the weights folder.


-------------------------------------------------------------------------------------------------------------------------
------------------------------------------------Steps for Prediction-----------------------------------------------------

1. Now to make the prediction video, just upload the video by the name of Clip.mp4 on Google Drive to be tracked of any 
   sport such as badminton, tennis etc.
2. Now, use the command specifying the path of the video and the path for the predicted video to be saved ,

 python  predict_video.py  --save_weights_path=weights/model.3 --input_video_path="./Clip.mp4" 
--output_video_path="./Clip_TrackNet.mp4" --n_classes=256 

3. Now wait for some minutes till the prediction process is complete depending upon the length of the video.
4. Download and play the predicted video to analyze the performance.


-------------------------------------------------------------------------------------------------------------------------
#########################################################################################################################