- [Video Instance Segmentation](#video-instance-segmentation)
  - [1. InstanceFormer: An Online Video Instance Segmentation Framework (AAAI2023)](#1-instanceformer-an-online-video-instance-segmentation-framework-aaai2023)
  - [2. VITA: Video Instance Segmentation via Object Token Association (NIPS2022)](#2-vita-video-instance-segmentation-via-object-token-association-nips2022)
  - [3. DeVIS: Making Deformable Transformers Work for Video Instance Segmentation (Arxiv2022)](#3-devis-making-deformable-transformers-work-for-video-instance-segmentation-arxiv2022)
  - [4. MinVIS: A Minimal Video Instance Segmentation Framework without Video-based Training (NIPS2022)](#4-minvis-a-minimal-video-instance-segmentation-framework-without-video-based-training-nips2022)
  - [5. IDOL: In Defense of Online Models for Video Instance Segmentation (ECCV2022)](#5-idol-in-defense-of-online-models-for-video-instance-segmentation-eccv2022)
- [Shadow Detection/Removal](#shadow-detectionremoval)
- [Tracking Any Point](#tracking-any-point)
  - [1. TAP-Vid: A Benchmark for Tracking Any Point in a Video (NIPS2022)](#1-tap-vid-a-benchmark-for-tracking-any-point-in-a-video-nips2022)
  - [2.  Particle Video Revisited: Tracking Through Occlusions Using Point Trajectories (ECCV2022)](#2--particle-video-revisited-tracking-through-occlusions-using-point-trajectories-eccv2022)


## Video Instance Segmentation
### 1. InstanceFormer: An Online Video Instance Segmentation Framework (AAAI2023)
[github](https://github.com/rajatkoner08/InstanceFormer)

<img width="1100" alt="instanceformer" src="https://user-images.githubusercontent.com/36613867/206744239-1f112fd9-259e-492f-9a48-7e1408985574.png">
A single-stage transformer-based efficient online VIS framework named InstanceFormer, which is especially suitable for long and challenging videos.

1. Eliminate the need for an external tracking head or data association.
3. Introduce a novel prior propagation module using reference points, class scores, and instance queries to enable efficient communication between consecutive frames.
4. Propose a novel memory module to which the current instance queries attend to recollect the recent past. Additionally, temporally contrastive training makes the memory discriminative and easy to identify.

### 2. VITA: Video Instance Segmentation via Object Token Association (NIPS2022)
[github](https://github.com/sukjunhwang/vita)

We proposed VITA for offline Video Instance Segmentation. VITA is a simple model built on top of the off-the-shelf image instance segmentation model (Mask2Former). Unlike existing offline methods, VITA directly leverages object queries decoded by independent frame-level detectors.

Specifically, we use an image object detector as a means of distilling object-specific contexts into object tokens. VITA accomplishes video-level understanding by associating frame-level object tokens without using spatio-temporal backbone features.

Moreover, thanks to its object token-based structure that is disjoint from the backbone features, VITA shows several practical advantages that previous offline VIS methods have not explored - handling long and high-resolution videos with a common GPU, and freezing a frame-level detector trained on image domain.

<img width="809" alt="VITA_2" src="https://user-images.githubusercontent.com/36613867/206921057-ce015907-9707-443c-b1ca-33e82ca3509b.png">
<img width="742" alt="VITA_1" src="https://user-images.githubusercontent.com/36613867/206921064-21a524fb-d748-4fd8-af1d-3e88e731b28d.png">

### 3. DeVIS: Making Deformable Transformers Work for Video Instance Segmentation (Arxiv2022)
[github](https://github.com/acaelles97/devis)

We present Deformable VIS (DeVIS), a VIS method which introduces temporal multi-scale deformable attention and instance-aware object queries.

We present a new instance mask prediction head which takes full advantage of deformable attention and encoded multi-scale feature maps.

Our improved multi-cue clip tracking incorporates mask and class information to connect overlapping clips to sequences of arbitrary length.

Related Works:
1. VisTR achieves communication between frames by concatenating and encoding the pixels of all frames jointly. Such a multi-frame processing only amplifies the expensive attention computation and makes [21] suffer from long training times and high memory requirements.
2. IFC [11] tries to mitigate these issues by introducing inter-frame memory tokens to encode each frame individually. However, [11] still relies on full attention for single frames and hence inherits the limitations of [5,21] to only process low- and single-scale feature maps.

<img width="781" alt="DeVIS_1" src="https://user-images.githubusercontent.com/36613867/207128307-4dcbd95d-13ff-480d-b467-005482ed7086.png">
<img width="776" alt="DeVIS_2" src="https://user-images.githubusercontent.com/36613867/207128347-562736b0-84b8-4b8c-9c46-016a89db4901.png">

### 4. MinVIS: A Minimal Video Instance Segmentation Framework without Video-based Training (NIPS2022)
[github](https://github.com/NVlabs/MinVIS)

We propose MinVIS, a minimal video instance segmentation (VIS) framework that achieves state-of-the-art VIS performance with neither video-based architectures nor training procedures. By only training a query-based image instance segmentation model, MinVIS outperforms the previous best result on the challenging Occluded VIS dataset by over 10% AP. Since MinVIS treats frames in training videos as independent images, we can drastically sub-sample the annotated frames in training videos without any modifications. With only 1% of labeled frames, MinVIS outperforms or is comparable to fully-supervised state-of-the-art approaches on YouTube-VIS 2019/2021. Our key observation is that queries trained to be discriminative between intra-frame object instances are temporally consistent and can be used to track instances without any manually designed heuristics. MinVIS thus has the following inference pipeline: we first apply the trained query-based image instance segmentation to video frames independently. The segmented instances are then tracked by bipartite matching of the corresponding queries. This inference is done in an online fashion and does not need to process the whole video at once.

![image](https://user-images.githubusercontent.com/36613867/207316720-2fa3b229-0b0c-410a-b4a8-9fc18b4973e3.png)
![image](https://user-images.githubusercontent.com/36613867/207316752-59283f77-85a6-46ca-bc2c-cfc4e3ae04c3.png)

### 5. IDOL: In Defense of Online Models for Video Instance Segmentation (ECCV2022)
[github](https://github.com/wjf5203/VNext)

We propose a framework In Defense of OnLine models for video instance segmentation, termed IDOL. The key idea is to ensure, in the embedding space, the similarity of the same instance across frames and the difference of differ- ent instances in all frames, even for instances that belong to the same category and have similar appearances.

However, previous method [30] selects positive and negative samples by a hand-craft setting, introducing false positives in occlusions and crowded scenes, thus impairing contrastive learning. To address it, we formulate the problem of sample selection as an Optimal Transport problem in Optimization Theory, which reduces false positives and further improves the quality of the embedding. During inference, by using one-to-many temporally weighted softmax, we utilize the learned prior of the embedding to re-identify missing instances caused by occlusions and to enforce the consistency and integrality of associations.

<img width="774" alt="image" src="https://user-images.githubusercontent.com/36613867/207661880-2bd364c0-035f-42b6-bbcf-e5ec4699c498.png">

## Shadow Detection/Removal


## Tracking Any Point
### 1. TAP-Vid: A Benchmark for Tracking Any Point in a Video (NIPS2022)
[github](https://github.com/deepmind/tapnet)

In this paper, we first formalize the problem, naming it tracking any point (TAP). We introduce a companion benchmark, TAP-Vid, which is composed of both real-world videos with accurate human annotations of point tracks, and synthetic videos with perfect ground-truth point tracks. Central to the construction of our benchmark is a novel semi-automatic crowdsourced pipeline which uses optical flow estimates to compensate for easier, short-term motion like camera shake, allowing annotators to focus on harder sections of video. We validate our pipeline on synthetic data and propose a simple end-to-end point tracking model TAP-Net, showing that it outperforms all prior methods on our benchmark when trained on synthetic data.

![image](https://user-images.githubusercontent.com/36613867/208254844-1ff4d470-d92b-483a-8c3d-44ed126fa949.png)

### 2.  Particle Video Revisited: Tracking Through Occlusions Using Point Trajectories (ECCV2022)
[github](https://github.com/aharley/pips)

We propose Persistent Independent Particles (PIPs), a method for multi-frame point trajectory estimation through occlusions. Our method combines cost volumes and iterative inference with a deep temporal network, which jointly reasons about location and appearance of visual entities across multiple timesteps. We argue that optical flow, particle videos, and feature matches cover different areas in the spectrum of pixel-level correspondence tasks. Particle videos benefit from temporal context, which matching-based methods lack, and can also survive multi-frame occlusions, which is missing in flow-based methods.

Our overall approach has four stages, somewhat similar to the RAFT optical flow method [32]: extracting visual features (Section 3.2), initializing a list of positions and features for each target (Section 3.3), locally measuring appearance similarity (Section 3.4), and repeatedly updating the positions and features for each target (Section 3.5). Figure 2 shows an overview of the method.