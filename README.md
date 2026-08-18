# deep-generative-ai-acp-design-tumour
Deep generative AI model for prediction of anticancer peptides against specific tumors.
# Deep Generative AI-Based Design of Anti-Cancer Peptides Against Specific Tumour Markers

## Overall Methodology

The project aims to develop a deep generative AI model for generating anti-cancer peptides (ACPs) against specific tumour markers. The methodology follows a sequential computational workflow involving ACP data collection, data processing and curation, tumour-marker identification, ESM-2-based sequence representation, Conditional Variational Autoencoder (CVAE) development, novel ACP generation, and downstream computational validation.

### Overall Workflow

TumorHoPe 2.0
        ↓
ACP Data Collection
        ↓
1,003 ACP Entries
        ↓
Python + Google Colab
Data Processing & Curation
        ↓
Remove Duplicates
Remove NA Entries
Remove Non-human ACPs
        ↓
Curated ACP Dataset
        ↓
Tumour-Marker Information
        ↓
Tumour Marker Name + Gene Symbol
+ UniProt ID + Tumour-Marker Sequence
        ↓
Integrated ACP–Tumour-Marker Dataset
        ↓
ESM-2
        ↓
ACP Sequence Embeddings
        ↓
Tumour-Marker Conditioning
        ↓
Conditional Variational Autoencoder (CVAE)
        ↓
Latent Space
        ↓
Novel ACP Generation
        ↓
In-silico Evaluation
        ↓
Molecular Docking
        ↓
Molecular Dynamics Simulation
        ↓
Final Candidate ACPs


## 1. Data Collection

A total of **1,003 experimentally reported anti-cancer peptide (ACP) entries** were collected from the **TumorHoPe 2.0 database using its REST API**.

The data collection was performed programmatically using Python packages in **Google Colab**.

The collected dataset contains information related to ACP sequences, cancer types, cell types, tumour markers, and other available experimental annotations.


## 2. Tumour-Marker Identification

The tumour markers associated with the collected ACPs were identified.

The corresponding **gene symbols, UniProt IDs, and tumour-marker protein sequences** were identified and incorporated into the dataset.

The relationship established in the curated dataset is:

ACP Sequence
        ↓
Tumour Marker
        ↓
Gene Symbol
        ↓
UniProt ID
        ↓
Tumour-Marker Protein Sequence


## 3. Data Processing and Curation

The collected data were processed and curated using Python packages in **Google Colab**.

The following preprocessing steps were performed:

- Removal of duplicate entries
- Removal of entries containing NA/missing values
- Removal of non-human ACP entries
- Organization of ACP information
- Organization of tumour-marker information
- Integration of ACP and tumour-marker information

The final curated dataset contains the following major features:

| Feature | Description |
|---|---|
| ACP Sequence | Amino-acid sequence of the anti-cancer peptide |
| Cancer Type | Cancer associated with the ACP |
| Cell Type | Target cell type/cell line |
| Tumour Marker Name | Associated tumour marker |
| Gene Symbol | Gene corresponding to the tumour marker |
| UniProt ID | Identifier of the tumour-marker protein |
| Tumour-Marker Sequence | Amino-acid sequence of the target protein |

The Python scripts used for data collection and preprocessing are maintained in this GitHub repository for reproducibility.


## 4. ESM-2 Sequence Representation

The curated ACP sequences will be processed using **ESM-2 (Evolutionary Scale Modeling-2)**, the pretrained protein language model selected for this project.

ESM-2 uses a Transformer-based architecture to learn contextual representations of protein sequences.

Each ACP sequence will be converted into a numerical embedding that captures meaningful sequence-level information.

The process can be represented as:

ACP Sequence
        ↓
ESM-2
        ↓
ACP Embedding

These embeddings will serve as the sequence representation for the subsequent generative modelling stage.


## 5. Conditional Variational Autoencoder (CVAE)

The ESM-2-derived ACP embeddings will be incorporated into a **Conditional Variational Autoencoder (CVAE)**.

The tumour marker will act as the **conditioning information**, while the ESM-2 representation will provide the learned representation of the ACP sequence.

The CVAE will learn the latent distribution of ACP representations associated with specific tumour-marker conditions.

During training:

ACP Sequence
        ↓
ESM-2
        ↓
ACP Embedding
        +
Tumour-Marker Condition
        ↓
CVAE Encoder
        ↓
Latent Representation
        ↓
CVAE Decoder
        ↓
Reconstructed / Generated ACP Representation


## 6. Novel ACP Generation

Once the CVAE has learned the relationship between ACP representations and tumour-marker conditions, it will be used to generate novel ACP candidates.

A selected tumour marker will be provided as the condition, and a latent representation will be sampled from the learned latent space.

The decoder will then generate a novel ACP candidate corresponding to the specified tumour marker.

The intended generation process is:

Tumour Marker
        +
Latent Representation
        ↓
CVAE Decoder
        ↓
Novel ACP Candidate


## 7. Negative Dataset

A separate negative/non-ACP dataset is **not required in the current generative modelling approach**.

The model will learn from the curated experimentally reported ACP dataset and generate novel candidates based on the learned ACP representation and tumour-marker condition.


## 8. In-silico Evaluation

The generated ACP candidates will undergo computational evaluation.

The candidates will be assessed based on relevant properties including:

- Sequence validity
- Novelty
- Diversity
- Physicochemical properties
- Predicted anti-cancer characteristics
- Toxicity
- Stability

Promising candidates will be shortlisted for further structural analysis.


## 9. Molecular Docking

The shortlisted ACP candidates will be subjected to **molecular docking** against their corresponding tumour-marker proteins.

Docking analysis will be used to investigate:

- Binding affinity
- Binding pose
- Peptide–tumour-marker interactions
- Interaction profile

The docking results will help identify ACP candidates with favourable interactions with their target tumour markers.


## 10. Molecular Dynamics Simulation

The most promising peptide–tumour-marker complexes will subsequently undergo **molecular dynamics (MD) simulations**.

MD simulations will be used to evaluate the structural stability and interaction behaviour of the peptide–target complexes.

Relevant parameters such as:

- RMSD
- RMSF
- Interaction stability
- Trajectory behaviour

will be analysed to identify stable peptide–tumour-marker complexes.


## Project Pipeline

The complete computational pipeline is:

**TumorHoPe 2.0 → 1,003 ACPs → Python/Google Colab preprocessing → Curated ACP–tumour-marker dataset → ESM-2 → ACP embeddings → Tumour-marker conditioning → CVAE → Novel ACP generation → In-silico evaluation → Molecular docking → Molecular dynamics simulation → Final candidate ACPs.**
