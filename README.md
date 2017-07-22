# car_det

We use py-faster-rcnn forked from [rbgirshick's work](https://github.com/rbgirshick/py-faster-rcnn) to do car detection.

This repo shows an example of car detection by finetuning a model using a new dataset.

### finetune

* Rename the layers to cls_score_car and bbox_pred_car
* Fine-tune pre-trained ImageNet model and snapshot at iteration 0. Let's call the snapshot Basketball_0.caffemodel. Stop training.
* Rename the layers back to cls_score and bbox_pred.
F* ine-tune Car_0.caffemodel to get the final model.

Reference: [Detection: Faster  R-CNN](https://huangying-zhan.github.io/2016/09/22/detection-faster-rcnn.html).
