# Awesome AI4Radiology

> A curated, paper-backed list of AI-based 3D radiological image reconstruction datasets, methods, codebases, and representation paradigms.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![Papers](https://img.shields.io/badge/papers-69-2ea44f)](#methods)
[![Datasets](https://img.shields.io/badge/datasets-21-0969da)](#datasets)
[![Code Links](https://img.shields.io/badge/code%20links-22-8a63d2)](#methods)
[![License](https://img.shields.io/github/license/Bean-Young/AI4Radiology)](LICENSE)
[![Stars](https://img.shields.io/github/stars/Bean-Young/AI4Radiology?style=social)](https://github.com/Bean-Young/AI4Radiology/stargazers)

This repository accompanies the systematic review **Representation Paradigms in AI-based 3D Radiological Image Reconstruction: A Systematic Review**.

The goal is simple: make it easy to find the right dataset, paper, and implementation for AI-based 3D reconstruction in CT, MRI, PET, SPECT, ultrasound, and multi-modality radiology.

## Contents

- [Highlights](#highlights)
- [Taxonomy](#taxonomy)
- [Datasets](#datasets)
- [Methods](#methods)
- [Evaluation Metrics](#evaluation-metrics)
- [Contributing](#contributing)
- [Citation](#citation)

## Highlights

- **Representation-first organization.** Methods are grouped by how the reconstructed target is parameterized, not only by network backbone.
- **Paper + code links.** Each method row includes a paper page and a code link when a public implementation is available.
- **Radiology-focused scope.** The list centers on reconstruction and image formation across CT, MRI, PET, SPECT, ultrasound, and multi-modality settings.
- **Awesome-style maintenance.** PRs adding missing code, paper pages, datasets, or corrected metadata are welcome.

## Taxonomy

| Family | Core idea | Typical strengths | Common limitations |
| --- | --- | --- | --- |
| Discrete grid | Reconstruct slices or volumes on regular pixels/voxels. | Simple, deployable, compatible with clinical image grids. | Fixed sampling can limit spatial continuity and memory efficiency. |
| Explicit basis expansion | Store finite coefficients over local bases, kernels, or transformed domains. | Interpretable coefficients and strong links to classical reconstruction. | Depends on basis/kernel design and imaging-operator conditioning. |
| Explicit primitive | Use adaptive primitives such as 3D Gaussians or meshes. | Efficient adaptive modeling and fast rendering potential. | Requires specialized initialization, rendering, and optimization. |
| Implicit neural | Model anatomy or measurements with continuous coordinate-query functions. | Strong continuous modeling under sparse-view or low-dose settings. | Expensive optimization and weaker interpretability. |

## Datasets

| Modality | Task | Dataset | Size | Details |
| --- | --- | --- | --- | --- |
| CT | Task I / Task II | AAPM Low Dose CT Grand Challenge | 30 abdominal cases plus an ACR phantom | A classic low-dose CT reconstruction benchmark providing quarter-dose and full-dose CT data for algorithm comparison under clinically relevant dose reduction. |
| CT | Task I / Task II | LDCT-and-Projection-Data | 299 clinical CT examinations | A TCIA/Mayo dataset containing head, chest, and abdomen CT projection data in DICOM-CT-PD format, with routine-dose and simulated low-dose projections for CT reconstruction and denoising. |
| CT | Task I / Task II | LoDoPaB-CT | 46,573 2D image-observation pairs | A large low-dose CT benchmark derived from LIDC-IDRI, providing simulated low-photon-count CT observations and ground-truth images for inverse reconstruction. |
| CT | Task I / Task III | SinoCT | >9,000 head CT scans | A large head CT dataset with reconstructed DICOM images and GE CatSim-simulated sinograms, suitable for sinogram-domain and reduced-projection CT reconstruction studies. |
| CT | Task II / Task III | AAPM CT-MAR Challenge | 14,000 training cases, 1,000 test cases, and 29 final clinical scoring cases | A CT metal artifact reduction benchmark providing paired metal-corrupted and metal-free images and sinograms, allowing image-domain, sinogram-domain, and hybrid reconstruction methods. |
| CT | Task I / Task III | MORE | 135 CT studies (65,575 slices) | A multi-organ CT reconstruction benchmark covering 9 anatomies and 15 lesion types, designed for sparse-view CT reconstruction and cross-anatomy generalization evaluation. |
| CT | Task III | Corona-Figueroa et al. | 25 CT volumes | A paper-specific chest and knee CT-to-DRR corpus used for single- or few-view X-ray/CT projection reconstruction and 3D-aware radiological novel-view synthesis. |
| MRI | Task I / Task III | fastMRI | 1,594 knee raw scans, 7,002 brain raw scans, plus prostate and breast subsets | A large-scale MRI reconstruction benchmark releasing raw k-space and reference images for accelerated single-coil and multi-coil MRI reconstruction. |
| MRI | Task I / Task III | Calgary-Campinas Public Brain MR Raw k-space Dataset | 167 3D T1-weighted brain MRI scans | A public brain MRI raw k-space benchmark with 12-channel and 32-channel acquisitions for accelerated 3D MRI reconstruction. |
| MRI | Task I / Task III | OCMR | 165 fully sampled and 212 prospectively undersampled cardiac cine series | An open-access cardiac MRI dataset providing multi-coil k-space data for fully sampled and prospectively undersampled cine reconstruction. |
| MRI | Task I / Task III | SKM-TEA | 155 qDESS knee MRI scans | A quantitative knee MRI dataset with raw k-space, reconstructed DICOM images, tissue segmentations, and pathology labels for end-to-end accelerated MRI reconstruction evaluation. |
| MRI | Task I / Task III | CMRxRecon2024 | 330 volunteers; 200/60/70 train/validation/test split | A multi-contrast, multi-view, multi-coil cardiac MRI k-space benchmark covering cine, mapping, tagging, flow, and dark-blood acquisitions with multiple undersampling patterns. |
| MRI | Task I / Task II | M4Raw | 183 healthy volunteers; >1,000 released volumes after quality control | A low-field 0.3T multi-channel brain MRI raw k-space dataset with T1w, T2w, and FLAIR repetitions for denoising, averaging, and parallel-imaging reconstruction. |
| PET | Task II | UDPET | 1,447 whole-body 18F-FDG PET subjects | A whole-body ultra-low-dose PET recovery benchmark providing low-statistics PET images at multiple dose-reduction factors aligned with full-dose PET images. |
| PET | Task I | PETRIC | Approximately 13 phantom datasets | A PET rapid image reconstruction challenge dataset with phantom list-mode files, attenuation-correction files, normalization/calibration files, vendor reconstructions, and VOIs for PET reconstruction benchmarking. |
| US | Task I / Task III | PICMUS | 4 core phantom datasets plus in-vivo carotid acquisitions | A canonical plane-wave ultrasound image-formation benchmark providing RF/IQ data from 75 steered plane waves for coherent compounding and beamforming reconstruction. |
| US | Task I / Task III | CUBDL | 576 ultrasound acquisition sequences | A large open ultrasound channel-data benchmark containing simulated, phantom, and in-vivo acquisitions for deep-learning-based beamforming and image formation. |
| US | Task III | Wysocki et al. / Ultra-NeRF | Synthetic liver sweeps and tracked spine-phantom sweeps | A B-mode ultrasound novel-view and volumetric representation dataset for learning view-dependent US image synthesis from overlapping sweeps. |
| PET / MRI | Task I | Monash vis-fPET-fMRI | 10 healthy adults | An OpenNeuro simultaneous FDG-fPET/BOLD-fMRI dataset releasing unreconstructed PET list-mode source data, normalization and sinogram-related files, and reconstructed PET images for PET reconstruction pipeline development. |
| PET / MRI | Task I | Monash DaCRA fPET-fMRI | 15 participants | An OpenNeuro FDG-fPET/fMRI dataset comparing bolus, infusion, and bolus-infusion protocols and releasing unreconstructed PET list-mode data for offline dynamic PET reconstruction. |
| SPECT / CT | Task I | Lu-177 DOTATATE Projection Data | 2 patients scanned at 4 post-therapy time points | A rare public human SPECT reconstruction dataset containing Lu-177 SPECT projection data and CT-based attenuation coefficient maps for quantitative SPECT reconstruction and dosimetry. |

## Methods

### Discrete grid representations

| Representation | Modality | Paper | Year | Code | Why it matters |
| --- | --- | --- | --- | --- | --- |
| Slice-wise | CT | [CTTR](https://www.sciencedirect.com/science/article/pii/S1120179722020154?casa_token=Mdbm9fp-4jUAAAAA:ii0SPXB6Gu78vHYhCDRpD_EnF1EgPgKwJkIuTFQt4bn3XafYjbAqZAPbTAx8X7zXPCQte1bo4LFw) | 2022 | - | A dual-domain transformer for sparse-view CT reconstruction. It restores sinogram and image-domain information while the final reconstruction remains an explicit CT grid. |
| Slice-wise | CT | [DuDoTrans](https://link.springer.com/chapter/10.1007/978-3-031-17247-2_9) | 2022 | [Code](https://github.com/mars11121/DuDoTrans.git) | A dual-domain transformer that restores sparse-view sinograms and reconstructs CT images by combining projection-domain and image-domain information. |
| Slice-wise | CT | [CoreDiff](https://arxiv.org/pdf/2304.01814) | 2023 | [Code](https://github.com/qgao21/CoreDiff) | A diffusion-based low-dose CT reconstruction method that uses a mean-preserving degradation process and image-domain restoration to suppress noise and preserve texture. |
| Slice-wise | MRI | [Du et al.](https://www.sciencedirect.com/science/article/pii/S0925231219304771) | 2020 | - | A residual CNN-based super-resolution method for anisotropic 3D MRI. Although the task targets 3D MRI, the network processes grid samples and outputs rasterized image slices. |
| Slice-wise | MRI | VarNet | 2020 | - | An end-to-end variational network for accelerated MRI reconstruction. It became a strong fastMRI baseline and reconstructs images on explicit sampled grids. |
| Slice-wise | MRI | [PCNN](https://analyticalsciencejournals.onlinelibrary.wiley.com/doi/abs/10.1002/nbm.4405) | 2021 | [Code](https://github.com/dsc936/rapid_recon_of_real-time_cine_using_PCNN.git) | A perceptual complex neural network for undersampled non-Cartesian cine MRI reconstruction, using complex convolutions and perceptual loss on discrete image grids. |
| Slice-wise | MRI | [SLATER](https://arxiv.org/pdf/2105.08059) | 2022 | [Code](https://github.com/icon-lab/SLATER) | An unsupervised adversarial transformer-based MRI reconstruction method that learns an image prior and performs zero-shot reconstruction on sampled image grids. |
| Slice-wise | CT/MRI | [MambaMIR](https://www.sciencedirect.com/science/article/pii/S1361841524002597) | 2025 | - | A Mamba-based medical reconstruction framework with arbitrary masking and uncertainty estimation, applied to fast MRI and sparse-view CT reconstruction. |
| Slice-wise | CT/MRI /PET | [Restore-RWKV](https://arxiv.org/pdf/2407.11087) | 2024 | [Code](https://github.com/Yaziwel/Restore-RWKV.git) | A medical image restoration model based on recurrent WKV attention and omnidirectional token shift. It handles CT, MRI, and PET restoration on discrete image grids. |
| Multi-plane | CT | Corona-Figueroa et al. | 2024 | - | A method that repeats and concatenates 2D X-ray views into a 3D volume representation and uses neural optimal transport to retain cross-view information. |
| Multi-plane | MRI | [MADGAN](https://link.springer.com/content/pdf/10.1186/s12859-020-03936-1.pdf) | 2021 | - | A GAN-driven method that uses multiple adjacent brain MRI slices to improve reconstruction and anomaly detection, making it more naturally a slice-stack grid representation. |
| Volume | CT | [HDNet](https://ieeexplore.ieee.org/abstract/document/9153172) | 2020 | - | A hybrid-domain neural network for sparse-view cone-beam CT reconstruction, combining projection and image-domain information in a volumetric grid output. |
| Volume | CT | [C2RV](https://openaccess.thecvf.com/content/CVPR2024/papers/Lin_C2RV_Cross-Regional_and_Cross-View_Learning_for_Sparse-View_CBCT_Reconstruction_CVPR_2024_paper.pdf) | 2024 | [Code](https://github.com/xmed-lab/C2RV-CBCT) | A cross-regional and cross-view learning framework for sparse-view CBCT reconstruction, using multi-scale volumetric representation and cross-view attention. |
| Volume | CT | Geometry-aware attenuation learning | 2024 | - | A sparse-view CBCT reconstruction method that encodes multi-view projections, back-projects features into 3D space, and decodes a voxel volume. |
| Volume | CT | DCT-Net | 2025 | - | A dual-branch CT reconstruction network from orthogonal X-rays, combining diffusion-based augmentation and perceptual contrastive learning for volumetric CT recovery. |
| Volume | MRI | [CINENet](https://www.nature.com/articles/s41598-020-70551-8.pdf) | 2020 | - | A 4D deep reconstruction framework for isotropic 3D cine MRI from single breath-hold acquisitions, reconstructing volumetric image sequences. |
| Volume | MRI | [Shaul et al.](https://www.sciencedirect.com/science/article/pii/S1361841520301110) | 2020 | [Code](https://github.com/ItamarDavid/Subsampled-Brain-MRI-Reconstruction-by-Generative-Adversarial-Neural-Networks.git) | A GAN-based undersampled MRI reconstruction framework combining U-Net and adversarial learning to recover high-quality grid-based MRI volumes. |
| Volume | PET | [DirectPET](https://www.spiedigitallibrary.org/journals/journal-of-medical-imaging/volume-7/issue-3/032503/DirectPET--full-size-neural-network-PET-reconstruction-from-sinogram/10.1117/1.JMI.7.3.032503.full) | 2020 | - | An end-to-end PET reconstruction method with a Radon inversion layer, designed for fast reconstruction from projection data to image grids. |
| Volume | PET | Xie et al. | 2021 | - | A supervised co-learning CNN framework that extracts PET and CT features and integrates them into constrained PET reconstruction to improve lesion contrast. |
| Volume | PET | [MEaTransGAN](https://www.sciencedirect.com/science/article/abs/pii/S1361841523002438) | 2024 | - | A 3D multi-modality Transformer-GAN that reconstructs standard-dose PET from low-dose PET and T1-weighted MRI. |
| Volume | PET | [Singh et al.](https://arxiv.org/pdf/2308.14190) | 2024 | [Code](https://github.com/Imraj-Singh/Score-Based-Generative-Models-for-PET-Image-Reconstruction.git) | A fully 3D PET reconstruction framework using score-based generative models and PET-specific sampling to improve robustness and image quality. |
| Volume | PET | Cycle-DCN | 2025 | - | A cycle-constrained adversarial denoising CNN for 3D low-dose PET image denoising, validated on large datasets with reader study and real low-dose data. The method operates on discrete volumetric PET images rather than continuous or primitive-based representations. |
| Volume | PET | DDPET-3D | 2026 | - | A dose-aware diffusion model for 3D low-dose PET denoising that generates consistent volumetric PET images across varying dose levels and improves image quality in ultra-low-dose settings. |
| Volume | SPECT | SPECTnet | 2021 | - | A deep learning method for direct SPECT reconstruction from projection data to high-resolution activity images. |
| Volume | CT/MRI | [DiffusionMBIR](https://openaccess.thecvf.com/content/CVPR2023/papers/Chung_Solving_3D_Inverse_Problems_Using_Pre-Trained_2D_Diffusion_Models_CVPR_2023_paper.pdf) | 2023 | [Code](https://github.com/HJ-harry/DiffusionMBIR) | A method combining pretrained 2D diffusion priors with model-based iterative reconstruction for sparse-view CT, limited-angle CT, and compressed sensing MRI. |

### Explicit basis expansion representations

| Representation | Modality | Paper | Year | Code | Why it matters |
| --- | --- | --- | --- | --- | --- |
| Local basis | PET | Mandeville et al. | 2024 | - | A recent PET study using B-spline basis functions for voxel-wise partial volume correction, showing that local basis representations remain relevant in reconstruction-related medical imaging problems. |
| Kernel coeff. | PET | [Gong et al.](https://papers.miccai.org/miccai-2024/paper/3664_paper.pdf) | 2021 | - | A direct parametric PET reconstruction method combining nonlocal deep image prior, a kernel matrix layer, and kinetic-model convolution. The reconstructed object remains a finite coefficient-based image. |
| Kernel coeff. | PET | [Li et al.](https://www.sciencedirect.com/science/article/abs/pii/S0169260724001068) | 2022 | - | A PET reconstruction framework that connects kernel representation with learnable deep mappings, improving dynamic PET reconstruction over empirical kernel construction. |
| Kernel coeff. | PET | Neural KEM | 2023 | - | A kernel expectation-maximization method with a deep coefficient prior, designed to improve low-count PET reconstruction while retaining explicit coefficient-space representation. |
| Kernel coeff. | PET | Guo et al. | 2023 | - | A PET reconstruction method that jointly regularizes image space and kernel space to reduce mismatch between anatomical priors and PET tracer distributions. |
| Kernel coeff. | PET | Deidda et al. | 2023 | - | A multimodal kernel-based reconstruction framework incorporating SPECT, PET, and CT side information, showing that kernel coefficient ideas extend beyond PET-only reconstruction. |
| Kernel coeff. | SPECT | Deidda et al. | 2022 | - | A hybrid kernelised expectation-maximisation method for Bremsstrahlung SPECT reconstruction, improving image resolution and noise properties with CT guidance. |

### Explicit primitive representations

| Representation | Modality | Paper | Year | Code | Why it matters |
| --- | --- | --- | --- | --- | --- |
| Gaussian | CT | [DIF-Gaussian](https://arxiv.org/pdf/2407.01090) | 2024 | [Code](https://github.com/xmed-lab/DIF-Gaussian) | A Gaussian-based sparse-view CBCT reconstruction method that learns 3D Gaussian features and optimizes them for extremely sparse projection settings. |
| Gaussian | CT | [R2-Gaussian](https://arxiv.org/pdf/2405.20693) | 2024 | [Code](https://github.com/Ruyi-Zha/r2_gaussian.git) | A radiative Gaussian splatting framework for tomographic reconstruction, designed to reduce integration bias and improve sparse-view reconstruction quality. |
| Gaussian | CT | [GaSpCT](https://arxiv.org/pdf/2404.03126) | 2024 | - | A Gaussian splatting framework for CT projection view synthesis from limited projections, improving efficiency compared with dense voxel and NeRF-style representations. |
| Gaussian | CT | [DDGS-CT](https://proceedings.neurips.cc/paper_files/paper/2024/file/456ce0476c9b4689a74918b851cecd5a-Paper-Conference.pdf) | 2024 | - | A direction-disentangled Gaussian splatting method for realistic CT volume rendering, decomposing radiosity into isotropic and directional components. |
| Gaussian | CT | X-Gaussian | 2025 | - | A radiative Gaussian splatting method for efficient X-ray novel-view synthesis, eliminating view dependency and improving training and inference speed. |
| Gaussian | CT | X-GRM | 2025 | - | A large Gaussian reconstruction model that decodes sparse-view X-rays into a voxel-based Gaussian representation for feed-forward CT reconstruction. |
| Gaussian | CT | [3DGR-CT](https://www.sciencedirect.com/science/article/abs/pii/S136184152500132X) | 2025 | [Code](https://github.com/SigmaLDC/3DGR-CT) | A sparse-view CT reconstruction method that initializes Gaussian primitives from FBP and updates them adaptively during self-supervised reconstruction. |
| Gaussian | CT | Fu et al. | 2025 | - | A 4D-CBCT reconstruction method that combines Gaussian primitives with deformation modeling to represent respiratory motion and dynamic anatomy. |
| Gaussian | MRI | CauGD2-Net | 2025 | - | A causality-driven dual-domain MRI reconstruction network enhanced by Gaussian-splatting-inspired spatial modeling to reduce artifacts and improve consistency. |
| Gaussian | MRI | 3DGSMR | 2025 | - | A 3D MRI reconstruction framework from undersampled k-space that represents the target MR volume with explicit 3D Gaussian primitives. |
| Gaussian | MRI | M-Gaussian | 2026 | - | A magnetic Gaussian framework for slice-to-volume MRI reconstruction that adapts 3D Gaussian primitives to efficient multi-stack MRI reconstruction. |
| Gaussian | PET | GR-Diffusion | 2026 | - | A whole-body PET reconstruction framework that combines explicit 3D Gaussian representation with diffusion-based refinement to improve global consistency and local detail recovery. |
| Gaussian | US | UltraGauss | 2025 | - | An ultrasound-specific Gaussian splatting framework for fast 3D ultrasound volume reconstruction, modeling probe-plane intersections to better match acoustic image formation. |
| Gaussian | US | UltraGS | 2025 | - | A depth-aware Gaussian splatting framework for ultrasound novel view synthesis, incorporating ultrasound-specific rendering effects such as attenuation, reflection, and scattering. |
| Gaussian | US | UltraG-Ray | 2026 | - | A physics-based ultrasound rendering method built on a learnable 3D Gaussian field, designed for realistic novel-view B-mode synthesis. |
| Simplex mesh | PET | Lesonen et al. | 2024 | - | A PET reconstruction method using anatomy-guided multi-resolution triangular meshes to achieve a favorable balance between accuracy and computational cost. |

### Implicit neural representations

| Representation | Modality | Paper | Year | Code | Why it matters |
| --- | --- | --- | --- | --- | --- |
| Coord. field | CT | Reed et al. | 2021 | - | An early medical INR method that reconstructs dynamic CT from limited views by combining a continuous neural field with parametric motion fields. |
| Coord. field | CT | [NAF](https://arxiv.org/pdf/2209.14540) | 2022 | [Code](https://github.com/Ruyi-Zha/naf_cbct) | A neural attenuation field method for sparse-view CBCT reconstruction, representing attenuation coefficients as a continuous function of 3D coordinates. |
| Coord. field | CT | [DIF-Net](https://arxiv.org/pdf/2303.06681) | 2023 | [Code](https://github.com/xmed-lab/DIF-Net) | A deep intensity field method for extremely sparse-view CBCT reconstruction, learning a continuous coordinate-to-intensity representation from sparse projections. |
| Coord. field | CT | [PINER](https://openaccess.thecvf.com/content/WACV2023/papers/Song_PINER_Prior-Informed_Implicit_Neural_Representation_Learning_for_Test-Time_Adaptation_in_WACV_2023_paper.pdf) | 2023 | [Code](https://github.com/efzero/PINER) | A prior-informed implicit neural representation method for test-time adaptation in sparse-view CT reconstruction. |
| Coord. field | CT | FACT | 2025 | - | A fast sparse-view CBCT reconstruction method using a meta-learned neural attenuation field and hash-encoding regularization. |
| Coord. field | MRI | IMJENSE | 2023 | - | A scan-specific INR framework for parallel MRI that jointly represents the image and coil sensitivity maps as continuous functions. |
| Coord. field | MRI | [NeSVoR](https://www.researchgate.net/profile/Junshen-Xu/publication/365043351_NeSVoR_Implicit_Neural_Representation_for_Slice-to-Volume_Reconstruction_in_MRI/links/636ab7c5431b1f53007e10d9/NeSVoR-Implicit-Neural-Representation-for-Slice-to-Volume-Reconstruction-in-MRI.pdf) | 2023 | [Code](https://github.com/daviddmc/NeSVoR) | An implicit neural representation method for slice-to-volume MRI reconstruction, recovering continuous fetal or neonatal MRI volumes from motion-corrupted slices. |
| Coord. field | MRI | Spatiotemporal INR for dynamic MRI | 2025 | - | A dynamic MRI reconstruction method that models the target sequence as a spatiotemporal coordinate field without requiring external training labels. |
| Coord. field | PET | IMREPET | 2025 | - | An unsupervised dynamic PET reconstruction method that parameterizes PET activity as a continuous spatiotemporal implicit neural representation. |
| Coord. field | US | [ImplicitVol](https://arxiv.org/pdf/2109.12108) | 2021 | - | A sensorless 3D ultrasound reconstruction method using deep implicit representation to learn a coordinate-to-intensity ultrasound volume. |
| Coord. field | CT/MRI | [NeRP](https://med.stanford.edu/content/dam/sm/dbds/XingSR1.pdf) | 2022 | [Code](https://github.com/liyues/NeRP) | A prior-embedded INR framework that maps spatial coordinates to image intensity values and uses prior images to improve sparse CT and MRI reconstruction. |
| Radiance field | CT | [MedNeRF](https://arxiv.org/pdf/2202.01020) | 2022 | [Code](https://github.com/abrilcf/mednerf) | A medical neural radiance field framework that reconstructs 3D-aware CT projections from single-view or few-view X-rays. |
| Radiance field | CT | [ACNeRF](https://iopscience.iop.org/article/10.1088/1361-6560/ad1d6c/meta) | 2024 | - | A medical NeRF method that improves single-view X-ray reconstruction by introducing alignment and pose correction for more accurate novel-view synthesis. |
| Radiance field | CT | [UMedNeRF](https://arxiv.org/pdf/2311.05836) | 2024 | - | An uncertainty-aware medical NeRF method for single-view volumetric rendering and CT projection synthesis. |
| Radiance field | CT | [VolumeNeRF](https://papers.miccai.org/miccai-2024/paper/3061_paper.pdf) | 2024 | [Code](https://www.github.com/Aurora132/VolumeNeRF) | A CT volume reconstruction method from a single projection view, integrating anatomical priors, projection attention, and Lambert-Beer law-based rendering. |
| Radiance field | CT | [SAX-NeRF](https://arxiv.org/abs/2311.10959) | 2024 | [Code](https://github.com/caiyuanhao1998/SAX-NeRF) | A structure-aware sparse-view X-ray 3D reconstruction method using radiance-field modeling with local and global ray sampling. |
| Radiance field | MRI | [CuNeRF](https://openaccess.thecvf.com/content/ICCV2023/papers/Chen_CuNeRF_Cube-Based_Neural_Radiance_Field_for_Zero-Shot_Medical_Image_Arbitrary-Scale_ICCV_2023_paper.pdf) | 2023 | [Code](https://NarcissusEx.github.io/CuNeRF) | A cube-based NeRF framework for zero-shot arbitrary-scale medical image super-resolution and free-view synthesis in CT and MRI. |
| Radiance field | MRI | Brain MRI NeRF reconstruction | 2023 | - | A NeRF-based method for reconstructing 3D-aware brain MRI representations from 2D MRI scans. |
| Radiance field | US | [Ultra-NeRF](https://proceedings.mlr.press/v227/wysocki24a/wysocki24a.pdf) | 2024 | - | A physics-aware ultrasound NeRF that models attenuation, reflection, and scattering to synthesize view-dependent B-mode images from tracked 2D ultrasound scans. |
| Radiance field | US | [UlRe-NeRF](https://arxiv.org/pdf/2408.00860) | 2024 | - | A 3D ultrasound neural rendering method that incorporates ultrasound reflection direction parameterization for improved view-dependent synthesis. |
| Radiance field | US | [NeRF-US](https://arxiv.org/pdf/2408.10258) | 2024 | [Code](https://rishitdagli.com/nerf-us/) | A neural radiance field framework designed to reduce ultrasound imaging artifacts and improve 3D ultrasound reconstruction in real-world settings. |

## Evaluation Metrics

| Category | Metrics |
| --- | --- |
| Pixel-wise error | MSE, RMSE, NRMSE, MAE |
| Signal and noise | PSNR, SNR, CNR |
| Perceptual / structural similarity | SSIM, LPIPS, FSIM, cosine similarity |
| Efficiency | Reconstruction time, rendering FPS, parameter count |

## Contributing

Help make this list more useful:

1. Add missing official paper pages, arXiv pages, project pages, and GitHub repositories.
2. Prefer official code links from authors over third-party reimplementations.
3. Keep entries concise and reconstruction-focused.
4. Open a PR with evidence when correcting metadata.

Suggested entry format:

```markdown
| Representation | Modality | Paper | Year | Code | Why it matters |
| --- | --- | --- | --- | --- | --- |
| Volume | CT | [Method Name](paper-url) | 2026 | [Code](repo-url) | One-sentence reconstruction-focused summary. |
```

## Citation

If this repository or the review helps your work, please cite:

```bibtex
@article{yang2026representation,
  title={Representation Paradigms in AI-based 3D Radiological Image Reconstruction: A Systematic Review},
  author={Yang, Yuezhe and Bi, Lei and Yang, Boyu and Wang, Yaqian and He, Yang and Peng, Yige and Jin, Zhe and Dong, Xingbo and Kim, Jinman},
  year={2026}
}
```
