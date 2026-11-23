# Research Proposal — Track A

**Student Name:** MUHAMMAD MASOOD KHAN  
**Registration No.:** 537713

## Title
**Robustness Evaluation of Open-Vocabulary Semantic Segmentation in Remote Sensing Images Using Test-Time Augmentation**

### 1. Benchmark paper
Kaiyu Li, Ruixun Liu, Xiangyong Cao, Xueru Bai, Feng Zhou, Deyu Meng, and Zhi Wang, “SegEarth-OV: Towards Training-Free Open-Vocabulary Segmentation for Remote Sensing Images,” *Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR)*, 2025, pp. 10545–10556.

- Paper: https://openaccess.thecvf.com/content/CVPR2025/html/Li_SegEarth-OV_Towards_Training-Free_Open-Vocabulary_Segmentation_for_Remote_Sensing_Images_CVPR_2025_paper.html
- DOI: https://doi.org/10.1109/CVPR52734.2025.00986
- Official code: https://github.com/likyoo/SegEarth-OV
- LoveDA dataset: https://zenodo.org/records/5706578

### 2. Problem and research gap
SegEarth-OV addresses low spatial detail in CLIP features and global-feature bias that can produce coarse shapes and poor boundaries. The project investigates a separate question: how stable are its predictions when the same aerial scene is viewed in a different orientation, and can combining predictions from two orientations improve accuracy enough to justify the extra computation? This is a focused evaluation gap for this project, not a claim that TTA itself is new or that no previous work has studied it.

### 3. Proposed extension: horizontal-flip TTA
I will first predict the original image. Then I will flip the same image left-to-right and run the same model again. I will flip the second class-score map back so both predictions align pixel by pixel. I will average the two score maps and select the highest-scoring class for each pixel. In simple terms, the model examines the same aerial scene from two directions and combines its predictions. This may reduce orientation-related errors, but it adds another forward pass and may increase inference time and GPU memory. Both the benefit and the cost will be measured.

### 4. Research question and evaluation
**Does horizontal-flip TTA improve SegEarth-OV’s mIoU and prediction consistency on LoveDA, and how much additional inference time and GPU memory does it require?**

Metrics: mIoU, class-wise IoU, orientation consistency (pixel agreement between original-view predictions and inverse-flipped predictions), average inference time, and peak GPU memory.

### 5. Completed work
The official demo notebook has been run in Google Colab on a Tesla T4. The environment initialized, CLIP ViT-B/16 loaded, the SimFeatUp checkpoint was found, and a single aerial-image prediction was generated. This is an initial demo, not a completed LoveDA benchmark reproduction.

### 6. Planned work
Verify the official LoveDA configuration and validation pipeline; prepare LoveDA; reproduce the paper’s LoveDA Table 1 result (36.9% mIoU); implement horizontal-flip TTA; compare baseline and TTA on identical data and settings; report accuracy, consistency, time, and memory. By 4 December, complete the pilot and attempt baseline evaluation. By 18 December, complete the extension, comparison, analysis, and report. If full validation is infeasible on Colab, compare both methods on the same documented subset and state the limitation.

### References
[1] K. Li et al., “SegEarth-OV: Towards Training-Free Open-Vocabulary Segmentation for Remote Sensing Images,” CVPR, 2025, pp. 10545–10556. DOI: 10.1109/CVPR52734.2025.00986.  
[2] J. Wang et al., “LoveDA: A Remote Sensing Land-Cover Dataset for Domain Adaptive Semantic Segmentation,” NeurIPS Datasets and Benchmarks, 2021.  
[3] S. Fu et al., “FeatUp: A Model-Agnostic Framework for Features at Any Resolution,” ICLR, 2024.  
[4] A. Radford et al., “Learning Transferable Visual Models From Natural Language Supervision,” ICML, 2021, pp. 8748–8763.
