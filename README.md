# Scene-Classification-and-Object-Detection-using-Caffe-and-YOLO
If you have Caffe and YOLO successfully installed on your system, you can proceed with scene classification using Caffe and YOLO on a webapp.
#### 1) Download the folder and unzip it.
#### 2) Open folder demo and place it in your /caffe-master/python directory
#### 3) Enter demo directory
- $ cd caffe-master
- $ cd python
- $ cd demo
#### 4) Create the following symbolic link in the  /caffe-master/python/demo directory :
- $ ln -s /home/username/caffe-master/python/caffe
#### 5) Ensure that you have the following files in your directories or edit the paths accordingly as our app.py requires each of the below mentioned files for running correctly.
- Line 135: /models/bvlc_reference_caffenet/deploy.prototxt
- Line 137: /models/bvlc_reference_caffenet/bvlc_reference_caffenet.caffemodel
- Line 139: /python/caffe/imagenet/ilsvrc_2012_mean.npy
- Line 141: /data/ilsvrc12/synset_words.txt
- Line 143: /data/ilsvrc12/imagenet.bet.pickle
### If the above files are not present, then simply run the following:
- $ cd caffe-master
- $ ./download_model_binary.py ../models/bvlc_reference_caffenet/
- $ ./data/ilsvrc12/get_ilsvrc_aux.sh
#### 6) Open app.py
Notes:
- Line 29 in app.py returns your home directory
- Line 29: userhome = os.path.expanduser('~')    
- Example: userhome value will be returned as /home/reena-mary

## Changes to be made in app.py
1) Lines 64, 97: Check if your prediction in darknet directory is a predictions.jpg file or a predictions.png file and edit the paths accordingly. This step is important. You need to ensure that the correct file type is present in your path (jpg or png).

2) Most likely, if Darknet is compiled with OpenCV, predictions.jpg will be present or if not,  predictions.png will be present in your darknet directory.

3) The code in app.py is applicable for a darknet folder that is in your Home Directory. If darknet is not in your Home directory, then, in Lines 64, 97 and 265, edit the path by appending your path after /home/username/ that leads to darknet directory in
- Line 64:  yolopred = userhome + "/darknet/predictions.jpg"
- Line 97:  yolopred = userhome + "/darknet/predictions.jpg"
- Line 265: req_path = userhome + "/darknet/"

 Example: yolopred = userhome + "/path between home directory and darknet/darkent/predictions.jpg"
### To run the program, 
- $ cd caffe-master
- $ cd python
- $ cd demo
- $ python app.py
###### If after a few runs, you get the error of "Port already in use", simply add the a new port as follows:
- $ python app.py -p 5001

On running the app.py, the webapp is automatically opened in your browser on http://0.0.0.0:5000 (Port number in the browser (here: 5000) changes as you change the port number while running the program.)
