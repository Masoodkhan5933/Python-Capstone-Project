# Research Proposal — Track A

## Robustness Evaluation of Open-Vocabulary Semantic Segmentation in Remote Sensing Images Using Test-Time Augmentation

### 1. Benchmark paper and resources
Kaiyu Li, Ruixun Liu, Xiangyong Cao, Xueru Bai, Feng Zhou, Deyu Meng, and Zhi Wang, “SegEarth-OV: Towards Training-Free Open-Vocabulary Segmentation for Remote Sensing Images,” *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, 2025, pp. 10545–10556. CVPR is a leading A* computer-vision venue.

- Paper: https://openaccess.thecvf.com/content/CVPR2025/html/Li_SegEarth-OV_Towards_Training-Free_Open-Vocabulary_Segmentation_for_Remote_Sensing_Images_CVPR_2025_paper.html
- DOI: https://doi.org/10.1109/CVPR52734.2025.00986
- Official code: https://github.com/likyoo/SegEarth-OV
- LoveDA dataset: https://zenodo.org/records/5706578

### 2. Result to reproduce
Reproduce the LoveDA semantic-segmentation result in Table 1 using mean Intersection over Union (mIoU). The paper reports **36.9% mIoU**. Use the authors’ released implementation, pretrained components, LoveDA validation data, and corresponding configuration. Document deviations and differences from the paper.

### 3. Research question and extension
**Does horizontal-flip test-time augmentation (TTA) improve SegEarth-OV’s mIoU on the LoveDA validation set compared with its original inference procedure, and what additional inference time and GPU memory does it require?**

Run inference on the original and horizontally flipped image, inverse-flip the second continuous class-score map, average the aligned maps, and decode the final prediction. Keep the baseline settings fixed. No model retraining is planned.

### 4. Work completed so far
The benchmark paper, official code, and LoveDA dataset have been selected. The authors’ demo notebook has been executed on a Tesla T4. Its recorded output shows the environment initialized, CLIP ViT-B/16 loaded, the SimFeatUp checkpoint present, and a single-image segmentation prediction generated. This is an initial inference pilot only. Full LoveDA validation, quantitative mIoU reproduction, and TTA experiments are not yet completed.

### 5. Data, implementation and evaluation
- **Data:** LoveDA aerial imagery and semantic masks.
- **Implementation:** Python, PyTorch, OpenCV/MMsegmentation, Google Colab; target GPU NVIDIA T4.
- **Baseline:** official SegEarth-OV configuration and pretrained CLIP/SimFeatUp components.
- **Extension:** horizontal-flip TTA.
- **Metrics:** mIoU, class-wise IoU, average inference time per image, peak GPU memory.

### 6. Timeline and fallback
- **By 4 December:** verify checkpoints and dataset preparation, complete an inference pilot, and run baseline validation if feasible.
- **By 18 December:** implement TTA, compare it fairly with the baseline, analyze results, and complete the report and repository.
- **Fallback:** if full validation is blocked by Colab runtime, memory, or dependency constraints, evaluate baseline and TTA on the same clearly identified smaller subset, document deviations, and do not claim full benchmark reproduction.

### References
[1] K. Li et al., “SegEarth-OV: Towards Training-Free Open-Vocabulary Segmentation for Remote Sensing Images,” CVPR, 2025, pp. 10545–10556. DOI: 10.1109/CVPR52734.2025.00986.  
[2] J. Wang, Z. Zheng, A. Ma, X. Lu, and Y. Zhong, “LoveDA: A Remote Sensing Land-Cover Dataset for Domain Adaptive Semantic Segmentation,” NeurIPS Datasets and Benchmarks, 2021.  
[3] A. Radford et al., “Learning Transferable Visual Models From Natural Language Supervision,” ICML, 2021, pp. 8748–8763.  
[4] S. Fu et al., “FeatUp: A Model-Agnostic Framework for Features at Any Resolution,” ICLR, 2024.

**Status:** Initial demo inference completed; full baseline reproduction and extension remain planned work.
