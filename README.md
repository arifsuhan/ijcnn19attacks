## For version upgrade, user may face various issue. That's why some codes are replaced or some are removed.

## Issues and Solutions

### File Path: src/cleverhans_tutorials/tsc_tutorial_keras_tf.py

***AttributeError: module 'keras.layers.core' has no attribute 'K'**
```
before: keras.layers.core.K.set_learning_phase(0)
after: tf.keras.backend.set_learning_phase(False)
```

***import settings***
```
import tensorflow.compat.v1 as tf
from tensorflow.compat.v1.keras import backend
```


***RuntimeError: This tutorial requires keras to be configured to use the TensorFlow backend.***
**113th to 126th lines**
```
    tf.keras.backend.set_learning_phase(False)

    if not hasattr(backend, "backend"):
      raise RuntimeError("This tutorial requires keras to be configured to use the TensorFlow backend.")

    if keras.backend.image_data_format() != 'channels_last':
      keras.backend.set_image_data_format('channels_last')
      print("INFO: '~/.keras/keras.json' sets 'image_dim_ordering' to 'th', temporarily setting to 'tf'")
              
    

    root_dir = 'data/dl-tsc/'
```

***AttributeError: module 'tensorflow' has no attribute 'Session'***
```
sess = tf.Session()
backend.set_session(sess)
```

### RuntimeError: tf.placeholder() is not compatible with eager execution.
```
tf.compat.v1.disable_eager_execution()
```

### TypeError: __init__() got an unexpected keyword argument 'ragged'
```
before: keras.models.load_model(file_path)
after: tensorflow.keras.models.load_model(file_path)
```


### File Path: src/cleverhans_copy/utils_keras.py
***TypeError: object of type 'InputLayer' has no len()***
```
before: import keras.*
after: import tensorflow.keras.*
```

## Setup 

### env
```
!pip install tensorflow==1.15.0
!pip install keras==2.2.4
```

### create directory for dataset and model 
```
import os
dataset_path = "data/dl-tsc/archives/TSC/HAR/"
pretrain_model_path = "data/dl-tsc/results/resnet/TSC/HAR/"

os.makedirs(pretrain_model_path)
```


### ijcnn19attacks/src/main.py
```
root_dir = 'data/dl-tsc'
archive_name = 'TSC'
```
