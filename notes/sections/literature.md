# Literature Review: Interpretable Feature Extraction from Protein Language Models

## Executive Summary

The field of interpretable protein language models has emerged as a critical research area at the intersection of machine learning and structural biology. Recent breakthroughs in sparse autoencoder (SAE) methodologies, particularly the InterPLM framework, have demonstrated the feasibility of extracting biologically meaningful features from transformer-based protein models. This literature review synthesizes current research across four key domains: (1) protein language model architectures and capabilities, (2) mechanistic interpretability techniques applied to biological sequences, (3) biological validation frameworks for model features, and (4) scalability challenges in large-scale protein analysis.

## 1. Protein Language Models: Foundations and Architectures

### 1.1 Transformer-Based Protein Language Models

The development of protein language models represents a paradigm shift from alignment-based methods to self-supervised learning on evolutionary sequences. **ESM-2** (Lin et al., 2023), developed by Meta AI, stands as the current state-of-the-art with models ranging from 8M to 15B parameters trained on 65 million protein sequences. The model demonstrates remarkable capability in learning evolutionary relationships and structural motifs directly from sequence data, achieving near-experimental accuracy in structure prediction through ESMFold.

**ProtBERT** and the ProtTrans family (Elnaggar et al., 2021) pioneered the application of BERT architectures to protein sequences, demonstrating that masked language modeling can capture biologically relevant patterns. These models showed early evidence that protein language models encode hierarchical biological information, from local motifs to global fold patterns.

**ProtFlash** (Li et al., 2023) and other recent architectures have focused on computational efficiency while maintaining biological relevance, addressing the scalability challenges inherent in large-scale protein analysis.

### 1.2 Architecture-Function Relationships

Recent comparative studies reveal architectural differences have profound implications for biological interpretability. Hýskova et al. (2025) conducted systematic benchmarking of AlphaFold2, ESMFold, and OmegaFold, revealing that **architectural choices directly influence which biological features are most effectively captured**. ESMFold's end-to-end design captures different structural patterns compared to AlphaFold2's MSA-dependent approach, suggesting that interpretability methods must be architecture-aware.

The scaling properties of protein language models follow distinctive patterns compared to natural language models. **Simon & Zou (2025) demonstrate that larger PLMs capture more interpretable biological concepts**, but the relationship is non-linear and subject to diminishing returns beyond certain parameter scales.

## 2. Mechanistic Interpretability in Protein Language Models

### 2.1 Sparse Autoencoder Approaches

The **InterPLM framework** (Simon & Zou, 2025) represents the first systematic application of sparse autoencoders to protein language models. Training SAEs on ESM-2 embeddings, the authors identified up to 2,548 interpretable features per layer, demonstrating strong correlation with 143 known biological concepts including binding sites, structural motifs, and functional domains. Critically, **individual neurons showed considerably less conceptual alignment (up to 46 neurons per layer across 15 concepts)**, providing strong evidence that PLMs store biological concepts in superposition.

**Adams et al. (2025)** extended this work in "From Mechanistic Interpretability to Mechanistic Biology," providing comprehensive training and evaluation protocols for SAEs on protein language models. Their work demonstrates that SAE features can be systematically characterized using biological databases and shows potential for scientific discovery through model interpretation.

### 2.2 Alternative Interpretability Methods

Beyond sparse autoencoders, several complementary approaches have emerged:

**Knowledge Neuron Identification**: Nori et al. (2023) applied activation-based and integrated gradient-based methods to identify "knowledge neurons" in ESM models, finding high density in key vector prediction networks of self-attention modules. This work suggests that **attention mechanisms in protein language models specialize in understanding different sequence features**.

**Categorical Jacobian Methods**: Zhang et al. (2024) developed gradient-based interpretability techniques that reveal how PLMs process functional categories, providing an alternative to sparse autoencoder approaches for understanding model representations.

### 2.3 Biological Validation of Interpretable Features

A critical challenge in protein interpretability is validating that extracted features correspond to genuine biological phenomena rather than statistical artifacts. **Silberg et al. (2025)** developed a comprehensive validation pipeline combining:

1. **Database Matching**: Integration across 20+ annotation sources including hierarchical biological codes
2. **Structural Consistency**: Feature-guided local structural alignment to verify activations correspond to consistent structural regions
3. **LLM-Based Description**: Automated feature characterization using large language models

Their work identified 615 SAE features with consistent structural similarity across unannotated metagenomic proteins, enabling structural annotation of at least 8,077 metagenomic sequences.

## 3. Biological Database Integration and Validation

### 3.1 Cross-Database Integration Challenges

Modern protein interpretability requires integration across multiple heterogeneous databases. **Choudhary et al. (2023)** provide unified access to residue-level annotations from UniProtKB, Pfam, SCOP, and PDB data, highlighting the complexity of cross-referencing biological annotations. Their work reveals significant gaps in annotation coverage, with many proteins lacking comprehensive functional characterization.

The **InterPro database** (Blum et al., 2025) serves as a crucial integration point, combining predictive signatures from multiple member databases to classify protein families. Recent updates incorporate AI-enhanced descriptions and increased AlphaFold structure integration, providing richer contexts for interpreting model features.

### 3.2 Missing Annotation Discovery

A significant contribution of interpretable PLMs is their capacity to identify missing database annotations. **The InterPLM work demonstrated automatic identification of at least 491 missing CATH topology annotations**, validating the biological utility of SAE features beyond existing knowledge.

This capability addresses a fundamental challenge in protein bioinformatics: the annotation gap between sequence discovery and functional characterization. Traditional homology-based methods fail for distant evolutionary relationships, while interpretable PLMs can identify conserved patterns that transcend sequence similarity.

### 3.3 Evolutionary Constraint Analysis

Recent work has begun connecting interpretable features to evolutionary constraints. **Feature consistency correlates with evolutionary conservation**, suggesting that interpretable PLM features capture functionally important sequence patterns maintained by natural selection. This connection provides additional validation for feature biological relevance and opens avenues for studying protein evolution through model interpretations.

## 4. Scalability and Architectural Considerations

### 4.1 Large-Scale Distributed Computing Approaches

Scaling interpretability methods to the full protein universe requires sophisticated computational strategies. **Zhong et al. (2022)** developed ParaFold for large-scale structure predictions, demonstrating approaches for parallelizing CPU-intensive MSA construction and GPU-based model inference. Their work provides a template for scaling interpretability analyses.

**van Kempen et al. (2023)** achieved clustering of 214 million protein structures using Foldseek, identifying 2.30 million non-singleton structural clusters. **31% of clusters lack functional annotations**, representing previously undescribed structural families. This work demonstrates the feasibility of proteome-scale analyses and reveals the scope of unknown protein space.

### 4.2 Computational Bottlenecks and Solutions

Current interpretability methods face several scalability challenges:

1. **Memory Requirements**: SAE training on large PLMs requires substantial GPU memory, limiting the size of models that can be interpreted
2. **Feature Attribution**: Computing feature activations across millions of proteins requires efficient attention mechanisms
3. **Biological Validation**: Cross-referencing features against multiple databases creates I/O bottlenecks

**Distributed approaches** using hierarchical sampling strategies and efficient computing protocols provide potential solutions, but require careful design to maintain biological validity.

### 4.3 Architecture-Specific Considerations

Different PLM architectures require tailored interpretability approaches:

- **ESM-2**: Dense representations benefit from sparse autoencoder decomposition
- **ProtBERT**: Attention pattern analysis reveals different biological patterns
- **ESMFold**: End-to-end structure prediction enables interpretability through geometric constraints

**Architecture comparison studies** (Manfredi et al., 2025; Simecek et al., 2025) suggest that interpretability methods must adapt to architectural differences to capture the full range of biological information encoded by different models.

## 5. Gaps and Future Directions

### 5.1 Methodological Gaps

Despite significant progress, several critical gaps remain:

1. **Cross-Architecture Interpretability**: Limited understanding of how biological features transfer between different PLM architectures
2. **Temporal Dynamics**: Static interpretability methods miss dynamic aspects of protein function
3. **Multi-Modal Integration**: Insufficient integration of sequence, structure, and functional data in interpretability frameworks

### 5.2 Biological Validation Limitations

Current validation approaches face several limitations:

1. **Database Bias**: Validation against existing databases may miss genuinely novel biological patterns
2. **Evolutionary Timescales**: Limited understanding of how interpretable features relate to evolutionary timescales
3. **Functional Context**: Difficulty validating features that depend on environmental or interaction contexts

### 5.3 Scalability Requirements

Achieving interpretability at the scale of the known protein universe requires:

1. **Computational Infrastructure**: Development of specialized hardware and algorithms for large-scale interpretability
2. **Database Integration**: Standardized approaches for integrating diverse biological databases
3. **Community Resources**: Shared platforms and datasets for reproducible interpretability research

## 6. Research Synthesis and Theoretical Framework

### 6.1 Emerging Theoretical Principles

The literature reveals several emerging theoretical principles:

1. **Superposition Hypothesis**: PLMs store biological concepts in distributed, overlapping representations rather than dedicated neurons
2. **Hierarchical Encoding**: Biological information is encoded hierarchically, from local motifs to global structural patterns
3. **Architecture-Biology Correspondence**: Different architectural patterns optimally capture different biological phenomena

### 6.2 Methodological Convergence

Multiple independent research groups have converged on similar methodological approaches:

1. **Sparse Autoencoder Decomposition**: SAEs provide the most effective method for extracting interpretable features
2. **Multi-Database Validation**: Comprehensive validation requires integration across multiple biological databases
3. **Automated Characterization**: LLM-based approaches enable scalable feature description and validation

### 6.3 Impact Assessment

The field has demonstrated clear impact across multiple domains:

1. **Scientific Discovery**: Identification of novel biological patterns invisible to traditional methods
2. **Database Enhancement**: Automated identification and correction of missing annotations
3. **Model Development**: Insights informing development of more interpretable and biologically-grounded PLMs

## Conclusion

The literature on interpretable protein language models reveals a rapidly maturing field with significant theoretical foundations and practical applications. The InterPLM framework and related sparse autoencoder approaches have established the feasibility of extracting biologically meaningful features at scale. However, critical challenges remain in biological validation, cross-architecture generalization, and computational scalability.

The convergence of multiple research groups on similar methodological approaches suggests robust underlying principles, while the diversity of applications demonstrates broad utility. The field is positioned for significant impact on both machine learning methodology and biological discovery, with the potential to transform how we understand and predict protein function.

Future research must address scalability challenges, develop more sophisticated validation frameworks, and explore the connection between interpretable features and evolutionary constraints. The integration of interpretability methods with experimental validation and the development of community resources will be critical for realizing the full potential of this emerging field.