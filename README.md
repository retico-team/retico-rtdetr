# retico-rtdetr
A ReTiCo module for the Real-Time DEtection TRansformer.

### Requirments  
This module relies on [retico-vision](https://github.com/retico-team/retico-vision).
- transformers  
- torch  

`pip install transformers torch`  

---
### Example
```python
import sys, os

prefix = '<path-to-retico-module-repositories>'

os.environ['RETICO'] = prefix + "retico-core"
os.environ['RETICOV'] = prefix + "retico-vision"
os.environ['RTDETR'] = prefix + "retico-rtdetr"

sys.path.append(os.environ['RETICO'])
sys.path.append(os.environ['RETICOV'])
sys.path.append(os.environ['RTDETR'])

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
This module is based on the RT-DETR vision model as introduced by Zhao et. al.
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
