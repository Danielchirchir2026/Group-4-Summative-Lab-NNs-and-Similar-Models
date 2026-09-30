# Group-4
# Summative Lab: NNs and Similar Models

## EcoSort Waste Management Assistant

An integrated AI-powered waste management assistant developed as a **group summative project**. The system combines image classification, text classification, Retrieval-Augmented Generation (RAG), and policy-based recycling guidance to help users identify waste and determine appropriate disposal methods.

---

## Project Overview

EcoSort is designed to assist residents of Metro City with proper waste disposal. The system accepts either an **image of a waste item** or a **text description**, identifies the waste category, retrieves relevant waste-management policies, and generates recycling or disposal instructions.

The project demonstrates the integration of:

* Convolutional Neural Networks (CNNs)
* Transfer learning using MobileNetV2
* Text classification using TF-IDF and Multinomial Naive Bayes
* Retrieval-Augmented Generation (RAG)
* Transformer-based text generation using FLAN-T5
* Policy-based information retrieval
* Integrated multimodal AI workflows

## Objectives

The main objectives of the project were to:

1. Classify waste materials from images.
2. Classify waste materials from text descriptions.
3. Retrieve relevant recycling and disposal policies.
4. Generate recycling instructions based on retrieved evidence.
5. Integrate all components into a unified waste-management assistant.
6. Evaluate the performance and limitations of the complete system.

## System Architecture

The EcoSort system follows the workflow below:

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
## Datasets

### RealWaste Image Dataset

The image component uses the **RealWaste dataset**, containing:

* **4,725 images**
* **9 waste categories**
* Relatively balanced category distribution
* Images resized to **224 × 224 pixels**
* Image augmentation applied during training

## Technologies Used

* Python
* Jupyter Notebook
* TensorFlow / Keras
* MobileNetV2
* Scikit-learn
* Pandas
* NumPy
* Matplotlib
* Seaborn
* TF-IDF
* Multinomial Naive Bayes
* Sentence Transformers
* FLAN-T5
* Retrieval-Augmented Generation (RAG)

---

## Project Structure

```text
EcoSort/
│
├── waste_management_summative.ipynb
│
├── RealWaste/
│   ├── Cardboard/
│   ├── Food Organics/
│   ├── Glass/
│   ├── Metal/
│   ├── Miscellaneous Trash/
│   ├── Paper/
│   ├── Plastic/
│   ├── Textile Trash/
│   └── Vegetation/
│
├── models/
│   └── ecosort_cnn_final.keras
│
├── data/
│   ├── text_dataset
│   └── policy_dataset
│
└── README.md
```

---

## How to Run the Project

### 1. Clone the repository

```bash
git clone <repository-url>
cd <repository-folder>
```

### 2. Install the required libraries

```bash
pip install numpy pandas matplotlib seaborn scikit-learn tensorflow
pip install sentence-transformers transformers
```

### 3. Open the Jupyter Notebook

```bash
jupyter notebook
```

Open:

```text
waste_management_summative.ipynb
```

### 4. Run the notebook

Run the cells sequentially from **Part 1 through Part 5**.

The notebook:

1. Loads and explores the datasets.
2. Preprocesses the image and text data.
3. Trains the CNN.
4. Fine-tunes the CNN.
5. Trains the text classifier.
6. Builds the RAG retrieval system.
7. Fine-tunes the instruction-generation model.
8. Integrates all components.
9. Evaluates the complete assistant.

---

## Example Usage

### Text Input

```python
description = (
    "An empty plastic water bottle that has been used "
    "and should be recycled."
)

result = waste_management_assistant(
    description,
    input_type="text"
)

display_assistant_response(result)
```

### Image Input

```python
result = waste_management_assistant(
    "path/to/waste_image.jpg",
    input_type="image"
)

display_assistant_response(result)
```

---

## Limitations and Future Improvements

The project identified several areas for further improvement:

* Improve image classification for visually similar waste categories.
* Increase the size and diversity of the image dataset.
* Improve confidence calibration for image predictions.
* Improve RAG grounding so generated instructions more closely follow retrieved policy evidence.
* Expand the policy corpus to cover more jurisdictions and waste-management scenarios.
* Improve handling of ambiguous waste descriptions.
* Conduct broader human evaluation of generated recycling instructions.
* Further optimize the integrated system for real-world deployment.

---

## Group Contribution

This project was completed as a **group summative lab for the NNs and Similar Models module**.

### Group Members

| Member   | Contribution   |
| -------- | -------------- |
| Member 1 | Daniel Chirchir |
| Member 2 | Patrick Patex |
| Member 3 | Daniel Tabut |
| Member 4 | Livingstone Talel |

> Replace the placeholders above with the actual group members and their contributions.

---

## Conclusion

The EcoSort project demonstrates how neural networks, traditional machine-learning techniques, semantic retrieval and generative AI can be combined to address a practical waste-management problem.

The completed system can accept **images or text descriptions**, identify the likely waste category, retrieve relevant policy information and generate recycling guidance. The evaluation demonstrates strong text-classification and retrieval performance, while also identifying image classification and RAG grounding as areas for continued development.

---

## Acknowledgements

This project was developed as part of the **Summative Lab: NNs and Similar Models** and uses the RealWaste dataset together with generated waste-management text and policy data provided for the project.
