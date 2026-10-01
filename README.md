# Group-4  Summative Lab: NNs and Similar Models

## EcoSort Waste Management Assistant

An integrated waste management assistant developed as a group summative project. The system combines image classification, text classification, Retrieval-Augmented Generation (RAG), and policy-based recycling guidance to help users identify waste and determine appropriate disposal methods.

---

## Project Overview

EcoSort is designed to assist residents of Metro City with proper waste disposal. The system accepts either an image of a waste item or a text description, identifies the waste category, retrieves relevant waste-management policies, and generates recycling or disposal instructions.

The project demonstrates the integration of:

- Convolutional Neural Networks (CNNs)
- Transfer Learning using MobileNetV2
- Text Classification using TF-IDF and Multinomial Naive Bayes
- Retrieval-Augmented Generation (RAG)
- Transformer-Based Text Generation using FLAN-T5
- Policy-Based Information Retrieval
- Integrated Multimodal AI Workflows

---

## Objectives

The main objectives of the project were to:

1. Classify waste materials from images.
2. Classify waste materials from text descriptions.
3. Retrieve relevant recycling and disposal policies.
4. Generate recycling instructions based on retrieved evidence.
5. Integrate all components into a unified waste-management assistant.
6. Evaluate the performance and limitations of the complete system.

---

## System Architecture

```text
                    User Input
                       |
             +---------+---------+
             |                   |
          Image                Text
             |                   |
             v                   v
       Fine-tuned CNN       Text Classifier
       (MobileNetV2)       (TF-IDF + Naive Bayes)
             |                   |
             +---------+---------+
                       |
                       v
                Waste Category
                       |
                       v
             Policy / RAG Retrieval
                       |
                       v
             Retrieved Evidence
                       |
                       v
          Instruction Generation
                 (FLAN-T5)
                       |
                       v
              Recycling Guidance
```

---

## Datasets

### RealWaste Image Dataset

The image component uses the RealWaste dataset containing:

- 4,752 verified images
- 9 waste categories
- Relatively balanced category distribution
- Images resized to 224 × 224 pixels
- Image augmentation applied during training

### Dataset Category Structure

The supplied project dataset was organised into the following nine categories:

- Cardboard
- Food Organics
- Glass
- Metal
- Miscellaneous Trash
- Paper
- Plastic
- Textile Trash
- Vegetation

All image-classification, text-classification, retrieval, and instruction-generation components were trained and evaluated using this consistent nine-category structure.

### Waste Description Dataset

The generated text dataset contains:

- 5,000+ waste-item descriptions
- Disposal instructions
- Material-composition information
- Common confusion cases
- Regional terminology variations

After preprocessing:

- 4,993 usable records
- Average description length of approximately 4.87 words
- Balanced category distribution

### Waste Policy Dataset

The policy corpus contains:

- 14 policy documents
- Municipal waste-management regulations
- Material sorting requirements
- Recycling and disposal guidance
- Policy updates and handling procedures

### Retrieval Corpus

The final RAG corpus combines:

- 14 policy documents
- 4,993 disposal-instruction records
- 5,007 retrieval records
- 384-dimensional semantic embeddings

---

## Technologies Used

- Python
- Jupyter Notebook
- TensorFlow / Keras
- MobileNetV2
- Scikit-learn
- Pandas
- NumPy
- Matplotlib
- Seaborn
- TF-IDF
- Multinomial Naive Bayes
- Sentence Transformers
- FLAN-T5
- Retrieval-Augmented Generation (RAG)

---

## Model Performance

### CNN Waste Classification

| Model | Test Accuracy |
|---|---:|
| Frozen MobileNetV2 | 78.82% |
| Fine-Tuned MobileNetV2 | 80.50% |

Most challenging categories:

- Miscellaneous Trash
- Plastic
- Glass

Best-performing categories:

- Vegetation
- Textile Trash
- Cardboard
- Paper

### Waste Description Classification

| Metric | Score |
|---|---:|
| Validation Accuracy | 99.73% |
| Test Accuracy | 98.93% |

Additional evaluation included:

- Confusion Matrix
- Precision, Recall, and F1 Analysis
- Keyword-Masked Robustness Test

### Integrated Assistant Evaluation

| Input Type | Sample Accuracy |
|---|---:|
| Image | 80% |
| Text | 100% |

---

## Project Structure

```text
EcoSort/
|
|-- EcoSort_Waste_Management_Summative.ipynb
|
|-- RealWaste/
|   |-- Cardboard/
|   |-- Food Organics/
|   |-- Glass/
|   |-- Metal/
|   |-- Miscellaneous Trash/
|   |-- Paper/
|   |-- Plastic/
|   |-- Textile Trash/
|   `-- Vegetation/
|
|-- models/
|   |-- ecosort_cnn_final.keras
|   `-- fine_tuned_recycling_generator/
|
|-- data/
|   |-- waste_descriptions.csv
|   `-- waste_policy_documents.json
|


---

## How to Run the Project
---
### 1. Clone the Repository

```bash
git clone <repository-url>
cd <repository-folder>

Note:
The fine-tuned FLAN-T5 model weights (model.safetensors) are not included in this repository because the file exceeds GitHub size limitations. The model can be recreated by running the fine-tuning notebook cells in Part 4.

```

### 2. Install Required Libraries

```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow
pip install sentence-transformers transformers datasets accelerate torch
```

### 3. Open the Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
EcoSort_Waste_Management_Summative.ipynb
```

### 4. Run the Notebook

Run the notebook sequentially from Part 1 through Part 5.

The notebook:

1. Loads and explores the datasets.
2. Preprocesses image and text data.
3. Trains the CNN classifier.
4. Fine-tunes the CNN.
5. Trains the text classifier.
6. Builds the semantic retrieval system.
7. Fine-tunes the FLAN-T5 generator.
8. Integrates all components.
9. Evaluates the complete assistant.

---

## Limitations and Future Improvements

The project identified several areas for further improvement:

- Improve image classification for visually similar waste categories.
- Increase the size and diversity of the image dataset.
- Improve confidence calibration for image predictions.
- Improve RAG grounding so generated instructions more closely follow retrieved policy evidence.
- Expand the policy corpus to cover more jurisdictions and waste-management scenarios.
- Improve handling of ambiguous waste descriptions.
- Conduct broader human evaluation of generated recycling instructions.
- Further optimise the integrated system for real-world deployment.
- Some retrieval results contained repeated disposal-instruction records, which occasionally reduced retrieval diversity.
- Future retrieval strategies should reserve at least one policy document during retrieval to strengthen factual grounding.
- Low-confidence image predictions can propagate errors into retrieval and instruction generation.

---

## Group Members

- Daniel Chirchir
- Patrick Patex
- Daniel Tabut
- Livingstone Talel

---

## Conclusion

The EcoSort project demonstrates how neural networks, traditional machine-learning techniques, semantic retrieval, and generative AI can be combined to address a practical waste-management problem.

The completed system can accept images or text descriptions, identify the likely waste category, retrieve relevant policy information, and generate recycling guidance.

---

## Acknowledgements

This project was developed as part of the Summative Lab: NNs and Similar Models and uses the RealWaste dataset together with generated waste-management text and policy data provided for the project.
