
# Tensorflow Object Detection API
## Setup guide for kaweesha
1. Create folder named `tensorflow1` in C: drive.
2. Download/Clone [tensorflow modals](https://github.com/tensorflow/models) to that folder.
3. Install [Anaconda](https://www.anaconda.com/download/) Python 2.7 one.
4. Open terminal and run command `conda create -n tensorflow1 pip python=2.7`
5. Run in same terminal `activate tensorflow1`
6. Run in same terminal `pip install --ignore-installed --upgrade tensorflow`
7. Run following commands in same terminal.
* `conda install -c anaconda protobuf`
* `pip install pillow`
* `pip install lxml`
* `pip install Cython`
* `pip install jupyter`
* `pip install matplotlib`
* `pip install pandas`
* `pip install opencv-python`
* `set PYTHONPATH=C:\tensorflow1\models;C:\tensorflow1\models\research;C:\tensorflow1\models\research\slim` *note that i'm assuming  'C:\tensorflow1' as tensorflow modals that downloaded 1st step located from now on*
* `cd C:\tensorflow1\models\research`
* `protoc --python_out=. .\object_detection\protos\anchor_generator.proto .\object_detection\protos\argmax_matcher.proto .\object_detection\protos\bipartite_matcher.proto .\object_detection\protos\box_coder.proto .\object_detection\protos\box_predictor.proto .\object_detection\protos\eval.proto .\object_detection\protos\faster_rcnn.proto .\object_detection\protos\faster_rcnn_box_coder.proto .\object_detection\protos\grid_anchor_generator.proto .\object_detection\protos\hyperparams.proto .\object_detection\protos\image_resizer.proto .\object_detection\protos\input_reader.proto .\object_detection\protos\losses.proto .\object_detection\protos\matcher.proto .\object_detection\protos\mean_stddev_box_coder.proto .\object_detection\protos\model.proto .\object_detection\protos\optimizer.proto .\object_detection\protos\pipeline.proto .\object_detection\protos\post_processing.proto .\object_detection\protos\preprocessor.proto .\object_detection\protos\region_similarity_calculator.proto .\object_detection\protos\square_box_coder.proto .\object_detection\protos\ssd.proto .\object_detection\protos\ssd_anchor_generator.proto .\object_detection\protos\string_int_label_map.proto .\object_detection\protos\train.proto .\object_detection\protos\keypoint_box_coder.proto .\object_detection\protos\multiscale_anchor_generator.proto .\object_detection\protos\graph_rewriter.proto`
* `python setup.py build`
* `python setup.py install`
8. Now copy files from my repo to your `C:\tensorflow1\models\research\object_detection` folder.
9. Run `python xml_to_csv.py` command to convert xml files in images/train and images/test into csv files in images/
10. Run `python generate_tfrecord.py --csv_input=images\train_labels.csv --image_dir=images\train --output_path=train.record` to generate 'train.record' with created 'images\train_labels.csv' file.
10. Run `python generate_tfrecord.py --csv_input=images\test_labels.csv --image_dir=images\test --output_path=test.record` to generate 'test.record' with created 'images\test_labels.csv' file.
11. Start training modal by running command `python train.py --logtostderr --train_dir=training/ --pipeline_config_path=training/faster_rcnn_inception_v2_pets.config`
12. After started you can start tensorboard by command `tensorboard --logdir=training` *Copy and paste the link generated in console to a web browser*
13. To test that generated modal by me. `python Object_detection_image.py`

*Each time you close a terminal and reopen you have to run command `set PYTHONPATH=C:\tensorflow1\models;C:\tensorflow1\models\research;C:\tensorflow1\models\research\slim`*
*Currently modal is only working better with cars only*
If you have question please ask from chathuranga. I'm much busy with work.