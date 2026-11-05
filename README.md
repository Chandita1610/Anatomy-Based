Anatomy-Grounded Vision–Language Transformer for Alzheimer's Disease Stage Classification from MRI
1. Overview
This repository presents an anatomy-grounded vision-language Transformer framework for Alzheimer's Disease (AD) stage classification using structural Magnetic Resonance Imaging (MRI). The proposed framework integrates hierarchical visual feature extraction, learned anatomical region discovery, region-specific semantic representation learning, visual–semantic grounding, and adaptive anatomy–semantic fusion. Unlike conventional image classification approaches that primarily rely on global visual representations, the proposed method explicitly learns disease-relevant anatomical representations associated with: Hippocampus, Ventricular system and Cerebral cortex. These anatomical representations are aligned with corresponding medical semantic concepts to improve classification performance and interpretability. The framework performs three-class classification: Cognitively Normal (CN), Mild Cognitive Impairment (MCI) and Extreme-Alzheimer's Disease (E-AD)

2. Key Contributions: The major contributions of this work are-
•	Anatomy-Grounded Vision–Language Learning: Integrates visual representation learning and medical semantic knowledge for MRI-based AD classification.
•	Learned Anatomical Region Discovery: Automatically identifies hippocampal, ventricular, and cortical attention regions without requiring manually annotated segmentation masks.
•	Region-Specific Semantic Grounding: Employs a trainable semantic Transformer and learned medical prototypes to establish anatomical visual–semantic correspondences.
•	Adaptive Anatomy–Semantic Fusion: Introduces a gated fusion mechanism to dynamically integrate anatomical visual and semantic representations.
•	Disease-Level Semantic Alignment: Incorporates disease-level semantic prototypes and supervised contrastive learning to improve class discrimination.
•	Anatomical Interpretability: Uses Grad-CAM visualization and counterfactual anatomical evidence analysis to investigate the contribution of individual brain regions.

4. Proposed Architecture<img width="3039" height="593" alt="Systematic_Overview" src="https://github.com/user-attachments/assets/94f4b621-5b4c-4acf-87b0-311c2e1c107f" />
Figure: Overall architecture of the proposed anatomy-based vision--language Transformer for Alzheimer's disease (AD) stage identification. The framework comprises five stages: (i) MRI preprocessing and anatomical-view generation, (ii) visual feature extraction and learned anatomical region discovery, (iii) region-specific semantic representation learning, (iv) anatomy--semantic fusion and disease-level representation learning, and (v) AD-stage classification and counterfactual anatomical evidence analysis. The model learns hippocampal, ventricular, and cortical representations and aligns them with region-specific medical semantic concepts to generate the final classification and anatomical evidence.

Stage 1: MRI Preprocessing and Anatomical View Generation
Stage 2: Visual Feature Extraction and Anatomical Region Discovery
Stage 3: Region-Specific Semantic Representation
Stage 4: Anatomy–Semantic Fusion and Disease-Level Representation
Stage 5: AD Classification and Anatomical Evidence Analysis

4. Datasets
The proposed framework is evaluated using two publicly available Alzheimer's disease MRI repositories:
Dataset	Description
ADNI	Alzheimer's Disease Neuroimaging Initiative
AIBL	Australian Imaging, Biomarker & Lifestyle Flagship Study of Ageing
Both datasets contain structural T1-weighted (T1w) and T2-weighted (T2w) MRI scans acquired using 3T scanners.
Dataset access:
•	ADNI: https://ida.loni.usc.edu/
•	AIBL: https://aibl.org.au/
Access to these datasets requires compliance with the respective repository licensing, registration, and data access policies.
Important: The original MRI datasets are not distributed through this GitHub repository.

5. Experimental Setup
The experimental configuration follows the settings reported in the manuscript.
Parameter	Configuration
Framework	PyTorch
Input image size	224 × 224
Visual feature dimension	384
Number of attention heads	6
MLP dimension	1536
Shifted-window Transformer blocks	4
Global Transformer blocks	4
Window size	7
Semantic Transformer layers	4
Semantic feature dimension	384
Optimizer	AdamW
Initial learning rate	2 × 10⁻⁴
Weight decay	1 × 10⁻⁴
Batch size	8
Maximum epochs	200
Learning-rate scheduler	Cosine Annealing
Training hardware	NVIDIA A100-PCIE-40GB
Automatic mixed precision, gradient scaling, and gradient clipping are used during training.
The dataset is divided into training, validation, and testing subsets using an 80:10:10 split.
Three random seeds (42, 123, and 2026) are used for the primary performance evaluation. Five additional seeds (10, 20, 30, 40, and 50) are used for statistical evaluation.

6. Installation
The framework is implemented using Python and PyTorch.
Create a virtual environment:
conda create -n anatomy_vit python=3.10
conda activate anatomy_vit
Install PyTorch according to your CUDA configuration:
pip install torch torchvision
Install commonly required scientific computing and image-processing libraries:
pip install numpy pandas scipy scikit-learn
pip install matplotlib seaborn
pip install opencv-python scikit-image
pip install Pillow tqdm
Note: The exact dependency versions should be specified in the repository's requirements.txt file after verifying the working environment.

7. Dataset Preparation
Download the required MRI data from the official ADNI and AIBL repositories after obtaining the necessary access permissions.
Prepare the MRI data according to the preprocessing pipeline described in the manuscript.
The processed data should contain the corresponding anatomical views and class labels.
The three paired anatomical configurations investigated in this study are: Ax_Cr, Ax_Sg and Cr_Sg
The exact directory structure should follow the dataset loader implemented in the repository.


8. Evaluation Metrics
The proposed framework is evaluated using the following metrics:
•	Accuracy
•	Sensitivity
•	Specificity
•	F1-score
•	Cohen's Kappa
•	Matthews Correlation Coefficient (MCC)
Additional evaluations include:
•	Calibration and reliability analysis
•	Decision Curve Analysis (DCA)
•	Ablation studies
•	Statistical significance testing
•	Computational complexity analysis



9. Ablation Studies
The contribution of the principal architectural components is investigated through four configurations:
•	Complete proposed framework.
•	Without learned ROI representation.
•	Without vision–language grounding.
•	Without region-dropout consistency.

The complete framework achieves:
•	Accuracy: 98.89%
•	F1-score: 98.86%
•	MCC: 98.60%

10. Explainability and Anatomical Analysis
The framework incorporates multiple interpretability approaches:
Grad-CAM: Visualizes spatial activation regions associated with model predictions.
Counterfactual Anatomical Evidence Analysis: Investigates the contributions of individual anatomical representations by selectively suppressing hippocampal, ventricular, and cortical features.
Perturbation-Based Faithfulness: Evaluates the sensitivity of model predictions after masking the top 20% of Grad-CAM activated pixels.
The reported mean confidence drop is 39.86 ± 52.28 percentage points.
These analyses provide complementary insights into the model's decision-making process. Grad-CAM visualizations should be interpreted as model attribution maps rather than anatomical segmentation masks.

11. Statistical Analysis
Statistical robustness is evaluated using:
•	Wilcoxon signed-rank test
•	Holm correction for multiple comparisons
•	Kruskal–Wallis test
•	McNemar's exact test
Statistical significance is considered at p < 0.05.

12. Code Availability
The implementation is publicly available at:
https://github.com/Chandita1610/Anatomy-Based.git
The repository provides the implementation associated with the proposed anatomy-grounded vision–language Transformer framework.

13. Contact
Chandita Barman
Department of Electronics and Communication Engineering
Indian Institute of Information Technology Guwahati
Guwahati, Assam, India.
Email: chandita.barman@iiitg.ac.in
Shovan Barma
Indian Institute of Information Technology Guwahati
Guwahati, Assam, India.

Acknowledgement: The authors acknowledge the ADNI and AIBL research initiatives for providing access to the MRI datasets used in this study.

