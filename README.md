# Paper-Reding-Hsing
## Video Instance Segmentation
### 1. [InstanceFormer: An Online Video Instance Segmentation Framework (AAAI2023)](https://arxiv.org/abs/2206.04403)
<img width="1100" alt="instanceformer" src="https://user-images.githubusercontent.com/36613867/206744239-1f112fd9-259e-492f-9a48-7e1408985574.png">
A single-stage transformer-based efficient online VIS framework named InstanceFormer, which is especially suitable for long and challenging videos.

1. Eliminate the need for an external tracking head or data association.
3. Introduce a novel prior propagation module using reference points, class scores, and instance queries to enable efficient communication between consecutive frames.
4. Propose a novel memory module to which the current instance queries attend to recollect the recent past. Additionally, temporally contrastive training makes the memory discriminative and easy to identify.

### 2. VITA: Video Instance Segmentation via Object Token Association

We proposed VITA for offline Video Instance Segmentation. VITA is a simple model built on top of the off-the-shelf image instance segmentation model (Mask2Former). Unlike existing offline methods, VITA directly leverages object queries decoded by independent frame-level detectors.


<img width="809" alt="VITA_2" src="https://user-images.githubusercontent.com/36613867/206921057-ce015907-9707-443c-b1ca-33e82ca3509b.png">
<img width="742" alt="VITA_1" src="https://user-images.githubusercontent.com/36613867/206921064-21a524fb-d748-4fd8-af1d-3e88e731b28d.png">
