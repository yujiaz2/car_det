# car_det

We use py-faster-rcnn forked from [rbgirshick's work](https://github.com/rbgirshick/py-faster-rcnn) to do car detection.

This repo shows an example of car detection by finetuning a model using a new dataset.

## finetune

* Rename the layers to cls_score_car and bbox_pred_car
* Fine-tune pre-trained ImageNet model and snapshot at iteration 0. Let's call the snapshot Basketball_0.caffemodel. Stop training.
* Rename the layers back to cls_score and bbox_pred.
* Fine-tune Car_0.caffemodel to get the final model.

** first finetune:

` 
$ ./tools/train_net.py --gpu 0 --weights data/imagenet_models/VGG16.v2.caffemodel --imdb car_train --cfg experiments/cfgs/config.yml --solver models/car/solver.prototxt --iter 0
` 

** second finetune:

` 
$ ./tools/train_net.py --gpu 0 --weights output/marker/car/train/vgg16_faster_rcnn_car_iter_0.caffemodel --imdb car_train --cfg experiments/cfgs/config.yml --solver models/car/solver.prototxt --iter 10000
` 

## evaluation and test

` ``
$ ./tools/test_net.py --gpu 0 --def models/car/test.prototxt --net output/marker/car/train/vgg16_faster_rcnn_car_iter_10000.caffemodel --imdb car_val --cfg experiments/cfgs/config.yml
` ``

Reference: [Detection: Faster  R-CNN](https://huangying-zhan.github.io/2016/09/22/detection-faster-rcnn.html).
