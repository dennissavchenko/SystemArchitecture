## Repository Description

This repository is a project designed to learn and practice creating system architecture diagrams and descriptions for an AI-based application. It includes:

- A detailed system architecture description.
- Images of the **System Architecture** and **Data Flow** diagrams to visually explain the workflow and relationships between components.
- A focus on designing a one-model AI system that integrates CoreML into an iOS application.

The goal is to explore and understand how various components of an AI system interact and how to document them effectively.

---

## System Architecture Description

The **BedTimeAI** application is designed as a single AI model system to predict the ideal bedtime based on user inputs like desired wake-up time, number of cups of coffee consumed, and desired hours of sleep. Below is an overview of its system architecture:

### Key Components

- **Public Dataset**:  
  A manually downloaded dataset from an open-source repository, serving as the initial source of training data.

- **Local Database**:  
  A storage system for both raw and processed (cleaned and standardized) datasets.

- **AI Model**:  
  A machine learning model trained to predict bedtime based on user inputs.

- **Python Script (`cleaning_and_standardization.py`)**:  
  Handles cleaning and standardization of both the public dataset and feedback data.

- **Feedback Processor**:  
  Processes user feedback, retrains the AI model, and updates the local database with the cleaned data.

- **UI**:  
  An iOS app, built using Swift, that allows users to interact with the AI model and provide feedback.

### Workflow Description

1. **Data Ingestion**:  
   - Data from a public dataset is manually downloaded from an open-source repository and loaded into the **Local Database**.

2. **Data Cleaning and Standardization**:  
   - A Python script (`cleaning_and_standardization.py`) is used to process raw data. This step includes cleaning and standardizing the dataset.  
   - The cleaned dataset is sent back to the **Local Database** for further use.

3. **Model Training and Testing**:  
   - The **AI model** is trained and tested using the cleaned and standardized data stored in the **Local Database**.  
   - The training process uses machine learning frameworks, and the final model is converted to the `.coreml` format for deployment with **CoreML**.

4. **Model Deployment**:  
   - The trained `.coreml` model is integrated into the **iOS app** and connected to the **UI**.  
   - Users interact with the model by providing inputs through the app, and the model predicts the optimal bedtime.

5. **Feedback Loop**:  
   - Users can provide performance feedback (e.g., whether the prediction was accurate).  
   - Feedback data is sent to the **Feedback Processor**, which:  
     a) Cleans and standardizes the feedback using the same Python script.  
     b) Uses the processed feedback to retrain the model.  
     c) Updates the **Local Database** with the new standardized data.

6. **Retraining**:  
   - The AI model is periodically retrained using feedback data to improve its predictions and adapt to user behavior over time.

### Technology Stack

- **CoreML**:  
  Used for deploying the trained model within the iOS app.

- **Swift**:  
  Language used to build the iOS user interface.

- **Python**:  
  Used for data cleaning, standardization, and feedback processing.
