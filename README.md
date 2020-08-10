## Multi-person Full Body Pose Estimation
The paper is accepted by imvip2020. [Here]() is our website.

### Get pseudo labels:
* Link：https://pan.baidu.com/s/1Fgkw9emYr6K7l5qGuVyAaQ

* Code：m6jn

### Get our model:
* Link: https://pan.baidu.com/s/1yQvPBXvXln69y3884MjDUQ

* Code: kihc

### Data format:
Our pseudo labels follows the format of [MSCOCO2017](https://cocodataset.org/#home). Each person has 133 keypoints, the first 17 are the original keypoints in COCO, the next 6 are foot keypoints, the next 68 are face keypoints, the next 21 are left hand keypoints and the last 21 are right hand keypoints.

### Train with [AlphaPose](https://github.com/MVIG-SJTU/AlphaPose/) and our pseudo labels:
- Clone AlphaPose and download our pseudo labels.
- Change the paths in 'AlphaPose/configs/coco/resnet/256x192_res50_lr1e-3_1x.yaml' and the num_joints to 133.
- Set EVAL_JOINTS in 'AlphaPose/alphapose/datasets/coco_det.py' and 'AlphaPose/alphapose/datasets/mscoco.py' to ```python list(range(133))```, and set the num_joints in 'AlphaPose/alphapose/datasets/mscoco.py' to 133.
- Set the joint_pairs in 'AlphaPose/alphapose/datasets/coco_det.py' and 'AlphaPose/alphapose/datasets/mscoco.py' to:
```python
        return[[1, 2], [3, 4], [5, 6], [7, 8], [9, 10], [11, 12], [13, 14], [15, 16], 
        [17, 20], [18, 21], [19, 22],[23, 39],[24,  38],[25, 37],[26, 36],[27, 35],
        [28, 34],[29, 33],[30, 32],[40, 49],[41, 48],[42, 47],[43, 46],
        [44, 45],[59, 68],[60, 67],[61, 66],[62, 65],[63, 70],[64, 69],
        [54, 58],[55, 57],[71, 77],[72, 76],[73, 75],[84, 86],[90, 88],
        [83, 87],[82, 78],[81, 79],[91, 112],[92, 113],[93, 114],[94, 115],
        [95, 116],[96, 117],[97, 118],[98, 119],[99, 120],[100, 121],[101, 122],
        [102, 123],[103, 124],[104, 125],[105, 126],[106, 127],[107, 128],[108, 129],
        [109, 130],[110, 131],[111, 132]]
```
- Then you can train a full body model. Turn to [AlphaPose](https://github.com/MVIG-SJTU/AlphaPose#quick-start) for more information about training.

### Inference using our model
- Set the num_joints in config file to 133 and set EVAL_JOINTS in 'AlphaPose/alphapose/utils/writer.py' to ```python list(range(133))```
- Change file 'AlphaPose/alphapose/utils/vis.py' into 133 keypoints case. You can visit [here](https://github.com/HaoyiZhu/AlphaPose/blob/master/alphapose/utils/vis.py) for reference.
- Then you can inference images or videos with 133 keypoints. Turn to [AlphaPose](https://github.com/MVIG-SJTU/AlphaPose#quick-start) for more information about inference.

### Results