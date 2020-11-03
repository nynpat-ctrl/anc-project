Source: https://www.analyticsvidhya.com/blog/2020/03/ball-tracking-cricket-computer-vision/

Input videos are provided in the given folder.
To run, 
First run 1.py (Where you specify which input video you want to run at the start of the code)
Then run 2.py (Where you spcify the name of the output video to be genrerated at the end)

'Data' folder will contain files which are used for training the model
'frames' folder will contain the all the frames extracted from the input video and which are later used to modify by highlighting the ball
'patch' folder will contain all the patches around the pitch where ball can be identified
'ball' folder will contain all the files where ball is identified

There will be 4 output images generated during the run as specified in the blog

By default I have used 8.mp4 video as the input and the attached images are for that video

The folders 'frames', 'ball' and 'patch' will be filled with image files when you run the code (By default they have files for 8.mp4 input)

I have also attached the output video I obtained after running 8.mp4 and 28.mp4 videos as 8_o.mp4 and 28_o.mp4 respectively

NOTE: 
As of now 2.py file will throw an error for MP4 cannot be supported as OpenCV does not support MP4 but that error can be removed by replacing output filename extension to '.avi'
Yet you will able to find mp4 output file in your folder and check the output generated. 