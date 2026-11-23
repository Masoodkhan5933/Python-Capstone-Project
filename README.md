# SegEarth-OV: Remote-Sensing Semantic Segmentation

Course project — **Track A (Research)**.

## Benchmark
**SegEarth-OV: Towards Training-Free Open-Vocabulary Segmentation for Remote Sensing Images** (CVPR 2025).

- Paper: https://openaccess.thecvf.com/content/CVPR2025/html/Li_SegEarth-OV_Towards_Training-Free_Open-Vocabulary_Segmentation_for_Remote_Sensing_Images_CVPR_2025_paper.html
- Official implementation: https://github.com/likyoo/SegEarth-OV
- LoveDA dataset: https://zenodo.org/records/5706578

## Research question
Does horizontal-flip test-time augmentation improve SegEarth-OV's mIoU on LoveDA, and what inference-time and GPU-memory overhead does it introduce?

## Planned experiments
1. Reproduce the official LoveDA baseline using the authors' configuration and pretrained components.
2. Add horizontal-flip TTA by inverse-flipping and averaging continuous class-score maps.
3. Compare mIoU, class-wise IoU, inference time, and peak GPU memory.

## Current status
The authors' demo has been run on a Tesla T4 and produced a single-image prediction. This is an initial inference pilot, **not** a completed LoveDA benchmark reproduction. Quantitative results will be added only after running the evaluation code.


Record the Git commit, Python/PyTorch/CUDA versions, GPU model, dataset split, config, checkpoint source, and command for each experiment. Do not commit dataset archives, model weights, credentials, or large generated files.

