# LSRNet

<div align="center">
  <img src="figs/example.png"/>
</div><br/>


## Introduction

(The code will be made available after acceptance of the paper).

## Supported datasets:
- [x] [Tusimple](configs/_base_/datasets/tusimple.py)
- [x] [CULane](configs/_base_/datasets/culane.py)


## Preparation
### Environments Preparation
Python == 3.8 \
CUDA == 11.1 \
pytorch == 1.9.1 \
mmcv-full == 1.5.1 \
mmdet == 2.25.0 

```Shell
python setup.py develop
```

### Data  Preparation
#### Tusimple
Download [Tusimple](https://github.com/TuSimple/tusimple-benchmark/issues/3).  Then extract them to `$TUSIMPLEROOT`. Create link to `data` directory.

```Shell
cd $LANEDET_ROOT
mkdir -p data
ln -s $TUSIMPLEROOT data/tusimple
```
For Tusimple, the segmentation annotation is not provided, hence we need to generate segmentation from the json annotation. 

```Shell
python tools/dataset_converts/generate_seg_tusimple.py --root $TUSIMPLEROOT
```

#### CULane

Download [CULane](https://xingangpan.github.io/projects/CULane.html). Then extract them to `$CULANEROOT`. Create link to `data` directory.

```Shell
cd $LANEDET_ROOT
mkdir -p data
ln -s $CULANEROOT data/CULane
```

For CULane, you should have structure like this:
```
$CULANEROOT/driver_xx_xxframe    # data folders x6
$CULANEROOT/laneseg_label_w16    # lane segmentation labels
$CULANEROOT/list                 # data lists
```


## Train & inference
```bash
# train
python tools/train.py [config/path_to_your_config]
# inference
python tools/test.py [config/path_to_your_config] [path_to_your_pth] --eval mAP
```


## Acknowledgement
Many thanks to the authors of [mmdetection](https://github.com/open-mmlab/mmdetection), [lanedet](https://github.com/Turoad/lanedet), [pytorch-auto-drive](https://github.com/voldemortX/pytorch-auto-drive) and [UnLanedet](https://github.com/zkyntu/UnLanedet).


