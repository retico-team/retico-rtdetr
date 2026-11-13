# retico-rtdetr
A ReTiCo module for the Real-Time DEtection TRansformer.

## Installation and Requirements

To use the RT-DETR module you first need to install the retico-rtdetr package:
* Install retico-rtdetr:
```pip install retico-rtdetr```

  or, for the latest development version from GitHub:
```pip install git+https://github.com/retico-team/retico-rtdetr.git```

## Modules

### `RTDETR`
Subscribes to `ImageIU` and outputs `DetectedObjectsIU` with the bounding boxes of the detected objects. The model is downloaded from Hugging Face and runs on the GPU if one is available, otherwise on the CPU. No IU is sent for images where nothing is detected.

#### Arguments:
* `model` (str): the model to use, `'r18'` or `'r50'`; defaults to `'r18'`
* `thresh` (float): the confidence threshold for a detection; defaults to `0.5`

### Example
**Note:** The example uses `WebcamModule` from [retico-vision](https://github.com/retico-team/retico-vision) and `DebugModule` from `retico_core`.

```python
from retico_core.debug import DebugModule
from retico_vision.vision import WebcamModule
from retico_rtdetr import RTDETR

webcam = WebcamModule()
rtdetr = RTDETR()
debug = DebugModule()

webcam.subscribe(rtdetr)
rtdetr.subscribe(debug)

webcam.run()
rtdetr.run()
debug.run()

input()

webcam.stop()
rtdetr.stop()
debug.stop()
```
---
### Citation
This module is based on the RT-DETR vision model as introduced by Zhao et al.
in the paper [DETRs Beat YOLOs on Real-time Object Detection](https://arxiv.org/abs/2304.08069),
under the [Apache-2.0 license](./LICENSE). For more information about the model and its authors,
please visit their [GitHub](https://github.com/lyuwenyu/RT-DETR?tab=readme-ov-file).

If you use `RT-DETR` or `RTDETRv2` in your work, please use the following BibTeX entries:
```latex
@misc{lv2023detrs,
      title={DETRs Beat YOLOs on Real-time Object Detection},
      author={Yian Zhao and Wenyu Lv and Shangliang Xu and Jinman Wei and Guanzhong Wang and Qingqing Dang and Yi Liu and Jie Chen},
      year={2023},
      eprint={2304.08069},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}

@misc{lv2024rtdetrv2improvedbaselinebagoffreebies,
      title={RT-DETRv2: Improved Baseline with Bag-of-Freebies for Real-Time Detection Transformer}, 
      author={Wenyu Lv and Yian Zhao and Qinyao Chang and Kui Huang and Guanzhong Wang and Yi Liu},
      year={2024},
      eprint={2407.17140},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2407.17140}, 
}
```
