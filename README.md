
# SMART-REQ: Automated Classification and Prioritization of Software Requirements

## **Introduction** 📘

Software requirement engineering is a critical phase of the software development lifecycle, guiding the implementation, testing, and deployment processes. Traditionally, requirement classification—dividing requirements into **Functional Requirements (FRs)** and **Non-Functional Requirements (NFRs)**—is done manually, leading to potential errors, inefficiencies, and inconsistencies.

**SMART-REQ** aims to automate the classification and prioritization of software requirements using advanced **Transformer-based models** like BERT, RoBERTa, and XLNet. This approach minimizes human effort while ensuring higher accuracy and scalability, making it invaluable for large-scale software projects.

### **Key Objectives**

- 🚀 Automate the classification of software requirements into Functional and Non-Functional categories.
- 📊 Further sub-categorize NFRs into **11 detailed subcategories**.
- 🤖 Leverage cutting-edge AI techniques to improve classification accuracy and scalability.
- 🔍 Provide actionable insights for better decision-making during the development process.

---

## **Features** ✨

### **1. Dual-Stage Classification**

- **Stage 1**: Binary classification into Functional and Non-Functional requirements.
- **Stage 2**: Multi-class classification of NFRs into:
  - Security
  - Usability
  - Performance
  - Scalability
  - Maintainability
  - Operability
  - Availability
  - Look-and-Feel
  - Fault Tolerance
  - Portability
  - Legal

### **2. Dataset Augmentation**

- Addressed class imbalance in NFR subcategories using **synthetic data generation with GPT-4**, increasing the dataset size from **525 to 1,671 NFR samples**.

### **3. Advanced NLP Models**

- Utilizes **BERT**, **RoBERTa**, and **XLNet** for superior context understanding and long-range dependency modeling.

### **4. PDF Parsing Capability**

- Processes multi-page PDF documents using the **LlamaParse API**, ensuring accurate classification even for complex layouts.

---

## **How It Works** ⚙️

### **Workflow**

1. **Input**: Accepts software requirements as plain text or PDF documents.
2. **Preprocessing**:
   - Text cleaning, tokenization, and augmentation.
   - Data is prepared for Transformer-based models.
3. **Classification**:
   - **Stage 1**: Classifies input as Functional or Non-Functional.
   - **Stage 2**: For NFRs, predicts one of 11 subcategories.
4. **Output**: Categorized and prioritized software requirements.

---

## **Project Contributions** 💡

### **Dataset**

The **PROMISE_exp dataset** was used as the baseline:

- **444 Functional Requirements.**
- **525 Non-Functional Requirements.**
- Augmented to **1,671 NFR samples** using GPT-4 to address class imbalance.

### **Preprocessing**

1. **Text Cleaning**: Removed contractions, punctuation, and stopwords.
2. **Tokenization**: Used BERT tokenizer for subword-level encoding.
3. **Label Transformation**: Converted categorical labels into numerical IDs for model compatibility.

### **Model Architecture**

- **Stage 1 Model**: Binary classification using BERT.
- **Stage 2 Model**: Multi-class classification using XLNet, RoBERTa, and BERT.

### **Evaluation Metrics**

- 📈 **Accuracy**: Indicates correctly classified instances.
- 📊 **F1 Score**: Provides a balanced view of Precision and Recall.
- 🧪 **Validation Loss**: Tracks performance across unseen data.

---

## **Results** 📊

### **Model Performance**

| **Metric**                             | **BERT** | **RoBERTa** | **XLNet** |
| -------------------------------------- | -------- | ----------- | --------- |
| **Binary Classification Accuracy (%)** | 90       | 87          | 80        |
| **Multi-Class F1 Score**               | 0.79     | 0.77        | 0.75      |
| **Validation Loss**                    | 0.74     | 0.94        | 0.89      |

### **Confusion Matrix**

**Binary Classification (Functional vs. Non-Functional):**

| True/Predicted     | Non-Functional | Functional |
| ------------------ | -------------- | ---------- |
| **Non-Functional** | 89             | 12         |
| **Functional**     | 8              | 85         |

**Multi-Class Classification (11 NFR Categories):**

| True Label \ Predicted Label | Security | Usability | Performance | Scalability | Maintainability | Operability | Availability | Look-and-Feel | Fault Tolerance | Portability | Legal |
|------------------------------|----------|-----------|-------------|-------------|-----------------|-------------|--------------|---------------|-----------------|------------|-------|
| **Security**                | 44       | 2         | 1           | 0           | 0               | 0           | 0            | 0             | 0               | 0          | 0     |
| **Usability**               | 1        | 35        | 0           | 0           | 0               | 1           | 0            | 5             | 0               | 0          | 0     |
| **Performance**             | 0        | 0         | 28          | 2           | 0               | 0           | 1            | 0             | 0               | 0          | 0     |
| **Scalability**             | 0        | 0         | 0           | 23          | 1               | 0           | 0            | 0             | 1               | 0          | 0     |
| **Maintainability**         | 0        | 0         | 0           | 1           | 21              | 3           | 0            | 0             | 0               | 1          | 0     |
| **Operability**             | 0        | 1         | 0           | 0           | 0               | 25          | 0            | 0             | 0               | 0          | 0     |
| **Availability**            | 0        | 0         | 0           | 0           | 0               | 0           | 13           | 0             | 0               | 0          | 0     |
| **Look-and-Feel**           | 0        | 1         | 0           | 0           | 0               | 0           | 0            | 3             | 0               | 0          | 0     |
| **Fault Tolerance**         | 0        | 0         | 0           | 0           | 0               | 0           | 0            | 0             | 3               | 0          | 0     |
| **Portability**             | 0        | 0         | 0           | 0           | 0               | 0           | 0            | 0             | 0               | 2          | 0     |
| **Legal**                   | 0        | 0         | 0           | 0           | 0               | 0           | 0            | 0             | 0               | 0          | 2     |

---

## **Setup Guide** 🛠️

### **Prerequisites**

1. **Environment**: Python 3.8 or higher.
2. **Dependencies**: Install required libraries using:
   ```bash
   pip install -r requirements.txt
   ```

### **Setting Up the Project**

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/YourUsername/SMART-REQ.git
   cd SMART-REQ
   ```

2. **Configure Environment Variables**:

   - Create a `.env` file in the root directory.
   - Add your LlamaParse API Key:
     ```plaintext
     LLAMA_PARSE=<your_llama_parse_api_key>
     ```

3. **Download Pretrained Model Weights**:

   - Place `bert.pt` in `phase1/` for binary classification.
   - Place `bert.pt` in `phase2/` for multi-class classification.

4. **Install Dependencies**:

   ```bash
   pip install -r requirements.txt
   ```

### **Running the Project**

#### **Training the Models**

1. Open `model_training.ipynb` in Jupyter Notebook or Google Colab.
2. Run all cells to train the models or load pretrained weights.

#### **Inference**

1. Use the `make_inference()` function in the notebook to classify software requirements:
   ```python
   make_inference(input_pdf_path="path/to/requirements.pdf")
   ```
2. The function generates:
   - Binary classification (FR vs. NFR).
   - Multi-class classification for NFR subcategories.

### **Testing with Sample Data**

1. Place your test requirements document (PDF or plain text) in the `data/test` folder.
2. Update the input path in `make_inference()` and execute.

---

## **Limitations** ⚠️

- **Overlapping NFRs**: Classification struggles when multiple NFRs appear on the same page.
- **Domain-Specific Jargon**: Ambiguity in highly technical terms can affect predictions.

---

## **Future Enhancements** 🌟

- Improved preprocessing for multi-page documents.
- Lightweight models for real-time deployment.
- Support for multi-language requirements.

---

## **Contributors** 🤝

- **Jaswant Vemulapalli** ([jvemula@umd.edu](mailto:jvemula@umd.edu))
- **Aanchal Pandey** ([apandey5@umd.edu](mailto:apandey5@umd.edu))
- **Piyush Anand** ([panand14@umd.edu](mailto:panand14@umd.edu))

---

## **License** 📜

This project is licensed under the MIT License.

---

### **Acknowledgments** 🙏

- This project leverages the **PROMISE_exp dataset** and incorporates insights from various academic papers on requirement engineering and NLP.
