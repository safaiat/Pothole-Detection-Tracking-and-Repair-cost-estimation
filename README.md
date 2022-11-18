Setting Up Environment
Using Conda
CPU
# CPU
conda env create -f conda-cpu.yml


# activate environment on Windows or Linux
conda activate tf-cpu

# activate environment on Mac
source activate tf-cpu
GPU
# GPU
conda env create -f conda-gpu.yml

# activate environment on Windows or Linux
conda activate tf-gpu

# activate environment on Mac
source activate tf-gpu
Using Pip
# CPU
pip install -r requirements.txt

# GPU
pip install -r requirements-gpu.txt
Note: If installing GPU version with Pip, you need to install CUDA and cuDNN in your system. You can find the tutorial for Windows here.

Download Weights File
Download yolov4.weights file 245 MB: yolov4.weights (Google-drive mirror yolov4.weights )

If using tiny version, download yolov4-tiny.weights file instead. tiny version is faster, but less accurate.

Convert YOLOv4 to TensorFlow
# Convert darknet weights to tensorflow
## yolov4
python save_model.py --weights ./data/yolov4.weights --output ./checkpoints/yolov4-416 --input_size 416 --model yolov4 

## yolov4-tiny
python save_model.py --weights ./data/yolov4-tiny.weights --output ./checkpoints/yolov4-tiny-416 --input_size 416 --model yolov4 --tiny
If you want to run yolov3 or yolov3-tiny change --model yolov3 in command and also download corresponding YOLOv3 weights and and change --weights to ./data/yolov3.weights

Run Tracking
# Run Tracking on Video
python track_objects.py --weights ./checkpoints/yolov4-416 --score 0.3 --video ./data/dog.mp4 --output ./results/demo.avi --model yolov4

# Run Tracking on Webcam
python track_objects.py --weights ./checkpoints/yolov4-416 --score 0.3 --video 0 --output ./results/webcam.avi --model yolov4

# Run Tracking on Video With Tiny Yolov4
python track_objects.py --weights ./checkpoints/yolov4-tiny-416 --score 0.3 --video ./data/dog.mp4 --output ./results/demo_tiny.avi --model yolov4

# Run Tracking on Webcam With Tiny Yolov4
python track_objects.py --weights ./checkpoints/yolov4-tiny-416 --score 0.3 --video 0 --output ./results/webcam_tiny.avi --model yolov4
Changing The Tracking Classes
You can change which classes should tracked by modifying data/classes/tracking.names file. By default, it only tracks person and dog classes.

Credits
hunglc007 Yolov4 TensorFlow Repo
nwojke DeepSort Repo
TheAIGuy DeepSort Repo
