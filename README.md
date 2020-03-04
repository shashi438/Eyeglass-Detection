# Eyeglass-Detection

Detect eye glasses using Python and tensorflow, starting with pre-trained weights of FaceNet


**Dependencies:**


Tensorflow 1.13

OpenCV 3.4.1

Python 3.7

## How to test:
We got accuracy of ~99% on the test set. 

Facenet originally has seperate training for classifier (SVM Classifier). We have eliminated this layer, removed the unnecessary losses
and made this end-to-end training, along with few necessary changes along the course of the project. 

**Path for testing** => ./facenet-modified/src/Final_test_model.py


**Path for model directory to load** => ./20190613-152417/ 


**Example of the command used:**


 python Final_test_model.py CLASSIFY /path/to/test/dataset/
 ./20190613-152417/ ./classifier_train/nonexis.pkl --batch_size 1000 --image_size 224

This command would load the model from directory, run it and give accuracy

### Dataset directory structure for testing:

    -->class1
    
      --> img1.jpg
      
      -->img2.jpg
      
    -->class2
     --> img1.jpg
      
      -->img2.jpg

********************************************************************

## Freezing, Optimizing and deploying models:

Frozen_model.pb is the frozen model generated from model files (.ckpt,.meta and .index) using
trnsfrm.py

inputs to this file: give model directory, and output node names. 

**command to run the above code:**
python trnsfrm.py --model_dir './20190613-152417/' --output_node_names 'output'


Frozen_inference_graph_dnn.pb is the model file stripped of all unused information like removing 
placeholders, optimizing batch normalization block etc
 (reference - https://medium.com/@dibyaranjan.sathua/how-to-use-tensorflow-graph-with-opencv-dnn-module-3bbeeb4920c5) 

command to run the code: 
In optim.py change line 201 and 203 (input graph from above step and output graph name to be saved)




