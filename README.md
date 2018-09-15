# Raccoon Detector Dataset

This is a dataset that I collected to train my own Raccoon detector with [TensorFlow's Object Detection API](https://github.com/tensorflow/models/tree/master/research/object_detection). Images are from Google and Pixabay. In total, there are 200 images (160 are used for training and 40 for validation).

## Getting Started

##### Folder Structure:
```

+ annotations: contains the xml files in PASCAL VOC format
+ data: contains the input file for the TF object detection API and the label files (csv)
+ images: contains the image data in jpg format
+ training: contains the pipeline configuration file, frozen model and labelmap
- a few handy scripts: generate_tfrecord.py is used to generate the input files
for the TF API and xml_to_csv.py is used to convert the xml files into one csv
- a few jupyter notebooks: draw boxes is used to plot some of the data and
split labels is used to split the full labels into train and test labels

-----
Copy your dataset to folder: xml file to annotations, images .jpg to images folder

```

##### Commands:
```
+ python xml_to_csv.py
+ Divide output_lables.csv thanhf 2 file train_lables.csv va test.csv
+ python generate_tfrecord.py --csv_input=data/train_labels.csv  --output_path=train.record
+ python generate_tfrecord.py --csv_input=data/test_labels.csv  --output_path=test.record

Copy folders: data, images, training, model, config file

+ protoc object_detection/protos/*.proto --python_out=.
+ export PYTHON_HOME=$PYTHON_HOME:`pwd`:`pwd`/slim (cd to the folder tensorflow/models/research)
+ python train.py --logtostderr --train_dir=training/ --pipeline_config_path=ssd_mobilenet_v1_pets.config  (cd to the folder tensorflow/models/research/object_detection)

+ python export_inference_graph.py --input_type image_tensor --pipeline_config_path ssd_mobilenet_v1_pets.config --trained_checkpoint_prefix training/model.ckpt-13302 --output_directory trained-inference-graphs/output_inference_graph_v1.pb

```

## Copyright

See [LICENSE](LICENSE) for details.
Copyright (c) 2017 [Dat Tran](http://www.dat-tran.com/).
