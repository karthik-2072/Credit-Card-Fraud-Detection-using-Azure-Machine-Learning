# Credit Card Fraud Detection using Azure Machine Learning

## Overview

This project focuses on developing a robust credit card fraud detection system using Azure Machine Learning. By leveraging Automated Machine Learning (AutoML) and custom pipelines, the project aims to efficiently handle and process data, select optimal models, and deploy a real-time inference system capable of detecting fraudulent transactions with high accuracy.

---

## Detailed Steps

### Azure Setup

1. **Create a Resource Group**:
   - Navigate to the [Azure portal home](https://portal.azure.com/).
   - Select **Resource Groups** and create a new resource group.

2. **Create Machine Learning Workspace**:
   - In the resource group, select **Machine Learning Workspace** and create a new workspace.
   - Provide necessary details such as workspace name, region, and resource group.

3. **Create Compute Resources**:
   - Under the **Manage** tab, create a compute instance for development.
   - Set up a compute cluster for model training by specifying the VM size and the number of nodes.

### Automated Machine Learning

1. **Initiate AutoML**:
   - Go to **Authoring > Automated ML** in the Azure Machine Learning workspace.
   - Create a new training job with a descriptive name and experiment name.
   - Add a description for better understanding and documentation.

2. **Dataset Setup**:
   - Upload your dataset in tabular format.
   - Choose the data source, such as local files or Azure Blob Storage, and upload the dataset (e.g., `credit_card_fraud.csv`).

3. **Configure Task Settings**:
   - Select the target column (`Class`) for prediction.
   - Choose the classification task for fraud detection.
   - Set up task settings including models to test, precision threshold (0.7), and experiment timeout (75 minutes).
   - Run the AutoML experiment to find the best performing model based on the set threshold and timeout.

### Custom Pipeline Creation

1. **Load Data**:
   - Import the dataset into the Azure Machine Learning Designer pipeline.
   - Use the **Import Data** module to load the data.

2. **Data Preprocessing**:
   - **Select Columns**:
     - Use the **Select Columns in Dataset** module to filter relevant features.
   - **Clean Missing Data**:
     - Apply the **Clean Missing Data** module to handle null values in the dataset.

3. **Data Transformation**:
   - **Normalize Data**:
     - Use the **Normalize Data** module to apply Min-Max scaling to the dataset.

4. **Data Splitting**:
   - Use the **Split Data** module to divide the dataset into training (70%) and testing (30%) sets.

5. **Model Training**:
   - Select an untrained model, such as **Decision Forest Regression**, from the module palette.
   - Connect the **Train Model** module to the untrained model and the training data.

6. **Model Scoring**:
   - Use the **Score Model** module to evaluate the model's performance on the test data.

7. **Model Evaluation**:
   - Assess the model using the **Evaluate Model** module, focusing on metrics such as AUC, precision, recall, and F1-score.

### Real-Time Inference Pipeline

1. **Pipeline Creation**:
   - Convert the trained model pipeline into a real-time inference pipeline.
   - Adjust the pipeline to accept new transaction data without the target column.

2. **Manual Data Input**:
   - Use the **Enter Data Manually** module to input new transaction data for prediction.

3. **Prediction and Output Validation**:
   - Predict fraud using the real-time inference pipeline and validate the output using the **Execute Python Script** module.

### Model Deployment

1. **Deploy the Model**:
   - Deploy the trained model to an Azure endpoint for real-time inference.
   - Ensure the deployment configuration supports scalability and reliability for handling live data.

---

## Conclusion

This project demonstrates the effective use of Azure Machine Learning for detecting credit card fraud. By combining Automated Machine Learning with custom pipelines, we achieved a high-performance model capable of real-time fraud detection. The step-by-step approach ensures a clear understanding of the entire machine learning workflow, from data preprocessing to model deployment.

---

