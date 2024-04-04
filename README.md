# DySample: Learning to Upsample by Learning to Sample

<p align="center"><img src="complexity.jpg" width="500" title="Complexity"/></p>

Code for the ICCV 2023 paper [Learning to Upsample by Learning to Sample](https://arxiv.org/abs/2308.15085).

We present DySample, an ultra-lightweight and effective dynamic upsampler. While impressive performance gains have been witnessed from recent kernel-based dynamic upsamplers such as CARAFE, FADE, and SAPA, they introduce much workload, mostly due to the time-consuming dynamic convolution and the additional sub-network used to generate dynamic kernels. Further, the need for high-res feature guidance of FADE and SAPA somehow limits their application scenarios. To address these concerns, we bypass dynamic convolution and formulate upsampling from the perspective of point sampling, which is more resource-efficient and can be easily implemented with the standard built-in function in PyTorch. We first showcase a naive design, and then demonstrate how to strengthen its upsampling behavior step by step towards our new upsampler, DySample. Compared with former kernel-based dynamic upsamplers, DySample requires no customized CUDA package and has much fewer parameters, FLOPs, GPU memory, and latency. Besides the light-weight characteristics, DySample outperforms other upsamplers across five dense prediction tasks, including semantic segmentation, object detection, instance segmentation, panoptic segmentation, and monocular depth estimation.

## Highlights

- **Fast:** DySample adopts very simple implementation for fast speed;
- **Easy to use:** DySample does not rely on any extra CUDA packages installed.

## Results

Object detection with Faster R-CNN on COCO
| Faster R-CNN | Backbone | Params |   AP     | $AP_{50}$ | AP$_{75}$ | AP$_S$   | AP$_M$   | AP$_{L}$ |  log  | ckpt  |
| :---:        |  :---:   | :---:  | :---:    | :---:     | :---:     | :---:    | :---:    | :---:    | :---: | :---: |
| Nearest      | R50      | 46.8M  | 37.4     | 58.1      | 40.4      | 21.2     | 41.0     | 48.1     |       |       |
| DySample     | R50      | +32.7K | 38.6     | 59.9      | 42.0      | 22.9     | 42.1     | 50.2     |[Link](https://github.com/tiny-smart/detection-with-upsamplers/releases/download/checkpoint/faster_rcnn_r50_fpn_dysample-lpg4_1x_coco.log)|[Link](https://github.com/tiny-smart/detection-with-upsamplers/releases/download/checkpoint/faster_rcnn_r50_fpn_dysample-lpg4_1x_coco.pth)|
| DySample+    | R50      | +65.5K | 38.7     | 60.0      | 42.2      | 22.5     | 42.4     | 50.2     |[Link](https://github.com/tiny-smart/detection-with-upsamplers/releases/download/checkpoint/faster_rcnn_r50_fpn_dysample-lpg4ds_1x_coco.log)|[Link](https://github.com/tiny-smart/detection-with-upsamplers/releases/download/checkpoint/faster_rcnn_r50_fpn_dysample-lpg4ds_1x_coco.pth)|

Instance segmentation with Mask R-CNN on COCO

## Citation
If you find DySample useful for your research, please cite:
```
@inproceedings{liu2023learning,
  title={Learning to Upsample by Learning to Sample},
  author={Liu, Wenze and Lu, Hao and Fu, Hongtao and Cao, Zhiguo},
  booktitle={Proc. IEEE/CVF International Conference on Computer Vision (ICCV)},
  year={2023}
}
```
