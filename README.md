# Master-Thesis: Adapting DINOv2 Embeddings for Fine-Grained Species Classification and Novelty Detection in Automated Moth Monitoring
**Autor:** Johannes Leick <br>
**Institution:** [Explainable Artificial Intelligence (xAI)](https://www.uni-bamberg.de/en/ai/chair-of-explainable-machine-learning/) at Otto Friedrich University of Bamberg

### Abstract:
This master’s thesis investigates and evaluates modern computer vision methods for the automated monitoring of moths. Given the context of global biodiversity loss and the need for scalable monitoring systems, this work assesses the suitability of self-supervised embeddings -- extracted from the DINOv2 (Small) foundation model -- to address challenges in Fine-Grained Visual Classification (FGVC), Domain Generalization (DG), and Novelty Detection (ND).

The AMI (Automated Monitoring of Insects) data source, characterized by high taxonomic diversity and varying image quality (high-resolution GBIF vs. low-resolution trap imagery), effectively representing real-world trap conditions. For this study, the AMI dataset was utilized in an adapted format at the species level, while its technical availability and suitability as a benchmark were simultaneously evaluated.

In the field of FGVC, utilizing embeddings on high-resolution imagery of 91 moth species demonstrates high recognition capabilities: a Multi-Layer Perceptron (MLP) achieved a Balanced Accuracy exceeding 94\%, outperforming a K-Nearest Neighbor (KNN) approach by 8 percentage points. The challenge of varying image quality (domain generalization) was evaluated by applying models trained on high-resolution data to low-resolution trap images (covariate shift). This resulted in a significant performance drop, with MLP accuracy falling below 45\%, though still maintaining an 8 percentage point lead over the KNN approach.

For novelty detection, a Deep K-Nearest Neighbor (DKNN) classifier was evaluated, utilizing density-based thresholds in embedding space to distinguish between 91 known species (In-Distribution) and 37 unknown (Out-of-Distribution) species. While an AUROC of 0.65 was achieved on high-resolution imagery, the detection performance degraded to near-chance level (AUROC 0.53) when evaluated under the domain shift of low-resolution trap images.

The cropping of rectangular images during feature vector extraction and the subsequent loss of information prompted the creation of a second, padded square image dataset. Compared to the original imagery, the squared dataset exhibited a performance degradation on all classifiers for high-resolution images, whereas a slight improvement was observed for low-resolution imagery.

Overall, the DINOv2 embeddings effectively captured fine morphological differences between 91 moth species within the high-resolution latent space. However, under domain shift, the compactness of the representations was significantly degraded, reducing class separability for both MLP and KNN models. In particular, the density-based DKNN approach to Novelty Detection (ND) failed in this scenario, as it was no longer possible to distinguish between 91 known and 37 unknown species.



### Quick start
1. Clone repository:
   ```bash
   git clone https://github.com/Johannesproximo/masterThesis.git
   ```
3. Set up environment:
   ```bash
   conda env create -f environment.yml
   ```
5. Activate environment:
   ```bash
   conda activate masterThesis
   ```
7. Adapt the paths in the Jupyter notebooks located in:

   `jupyter_notebooks/*`

   For example, start with the notebook for image downloads:

   `jupyter_notebooks/00_download_image_high/fine_grain/0_download_images.ipynb`

8. Run Jupyter notebooks


### Dependencies

The environment is based on **Python 3.12** and includes the following core libraries  
(managed via `environment.yml`):
- **Data Science:** pandas, scikit-learn, seaborn, opencv  
- **Deep Learning:** pytorch, timm  
- **Specialized:** python-dwca-reader, webdataset, nbconvert, conda-forge::lz4
