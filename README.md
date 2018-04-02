<<<<<<< HEAD
# SSD: Single Shot MultiBox Detector

[![Build Status](https://travis-ci.org/weiliu89/caffe.svg?branch=ssd)](https://travis-ci.org/weiliu89/caffe)
[![License](https://img.shields.io/badge/license-BSD-blue.svg)](LICENSE)

Original work by [Wei Liu](http://www.cs.unc.edu/~wliu/), [Dragomir Anguelov](https://www.linkedin.com/in/dragomiranguelov), [Dumitru Erhan](http://research.google.com/pubs/DumitruErhan.html), [Christian Szegedy](http://research.google.com/pubs/ChristianSzegedy.html), [Scott Reed](http://www-personal.umich.edu/~reedscot/), [Cheng-Yang Fu](http://www.cs.unc.edu/~cyfu/), [Alexander C. Berg](http://acberg.com).


### Contents
1. [Installation](#installation)
2. [Preparation](#preparation)
3. [Train/Eval](#traineval)

### Installation
1. Get the code. We will call the directory that you cloned Caffe into `$CAFFE_ROOT`
  ```Shell
  git clone https://github.com/minhnguyen18/ssd_checkerboard.git
  cd caffe
  git checkout ssd
  ```
2. Build the code. Please follow [Caffe instruction](http://caffe.berkeleyvision.org/installation.html) to install all necessary packages and build it.
  ```Shell
  # Modify Makefile.config according to your Caffe installation.
  cp Makefile.config.example Makefile.config
  make -j8
  # Make sure to include $CAFFE_ROOT/python to your PYTHONPATH.
  make py
  make test -j8
  # (Optional)
  make runtest -j8
  ```

### Preparation
Assuming that data root is $DATA_ROOT = $HOME/data/
1. Images are taken with Pi camera and stored at $DATA_ROOT/checkerboard/Images.
2. Bounding boxes are defined and images are labelled with the tool which can be downloaded from https://github.com/tzutalin/labelImg. The tool will create VOC data. You can refer to the guidance here https://github.com/jinfagang/kitti-ssd.
3. Create the LMDB file.
  ```Shell
  cd $CAFFE_ROOT
  # Create the trainval.txt, test.txt, and test_name_size.txt in $DATA_ROOT/checkerboard/Images. The images will be shuffled.
  bash data/checkerboard/create_list.sh
  # You can modify the parameters in create_data.sh if needed.
  # It will create lmdb files for trainval and test with encoded original image:
  #   - $DATA_ROOT/checkerboard/lmdb/checkerboard_trainval_lmdb
  #   - $DATA_ROOT/checkerboard/lmdb/checkerboard_test_lmdb
  # and make soft links at examples/checkerboard/
  bash data/checkerboard/create_data.sh
  ```

### Train/Eval
1. Train your model and evaluate the model on the fly.
  ```Shell
  # It will create model definition files and save snapshot models in:
  #   - $CAFFE_ROOT/models/VGGNet/checkerboard/SSD_300x300/
  # and job file, log file, and the python script in:
  #   - $CAFFE_ROOT/jobs/VGGNet/checkerboard/SSD_300x300/
  # and save temporary evaluation results in:
  #   - $HOME/data/VOCdevkit/results/checkerboard/SSD_300x300/
  python examples/checkerboard/ssd_checkerboard.py
  # You can modify the parameters according to the model you want to train, e.g. `max_iter`, `num_classes`, `background_index_id`, ...
  ```
2. Test your model using still image. Note: press <kbd>enter</kbd> to stop.
  ```Shell
  # If you would like to test a model you trained with an image, you can do:
  python examples/checkerboard/checkerboard_detection.py
  # Replace the image name with the name of your image
  ```
=======
# ssd_checkerboard
>>>>>>> 255da3fc4cd25a0023c5858f898c099dfb8aca2a

### Citing SSD
    @inproceedings{liu2016ssd,
      title = {{SSD}: Single Shot MultiBox Detector},
      author = {Liu, Wei and Anguelov, Dragomir and Erhan, Dumitru and Szegedy, Christian and Reed, Scott and Fu, Cheng-Yang and Berg, Alexander C.},
      booktitle = {ECCV},
      year = {2016}
    }
