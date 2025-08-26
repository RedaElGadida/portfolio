# Car Damage Severity Detection with Vertex AI

## Project Overview

This project demonstrates a complete, cloud-based computer vision workflow using Google Cloud's Vertex AI platform. The goal is to build, train, and deploy an AutoML image classification model capable of detecting the severity of car damage (`minor`, `moderate`, `severe`) from an image.

This project showcases a modern, end-to-end MLOps process, from data preparation in the cloud to deploying a live prediction endpoint.

---
## Dataset

This project utilizes the **Car Damage Severity Dataset** from Kaggle. The dataset contains hundreds of images of cars, pre-sorted into three categories based on the level of damage:
* `01-minor`
* `02-moderate`
* `03-severe`

The data is split into `training` and `validation` sets.

---
## Methodology

The entire project was built using the Vertex AI Python SDK, following these key steps:

1.  **Environment Setup:** Authenticated a local Jupyter Notebook environment to securely interact with Google Cloud Platform services.
2.  **Data Preparation & Upload:**
    * A new **Google Cloud Storage (GCS) bucket** was created to host the image dataset.
    * The entire local dataset was uploaded to the GCS bucket, preserving the `training/label/image.jpg` structure.
    * A `dataset.csv` index file was programmatically generated to reliably map each image's cloud storage path to its correct label.
3.  **Vertex AI Dataset Creation:** A managed `ImageDataset` resource was created in Vertex AI, pointing to the `dataset.csv` file in the GCS bucket.
4.  **AutoML Model Training:**
    * An `AutoMLImageTrainingJob` was launched using the created dataset.
    * Vertex AI automatically handled the model selection, training, and tuning process with a budget of 8 node-hours to stay within the free tier.
5.  **Deployment & Prediction:**
    * The successfully trained model was deployed to a live **Vertex AI Endpoint**.
    * A real-time prediction was made by sending a new, unseen image from the validation set to the deployed endpoint.
6.  **Cleanup:** All created cloud resources (Endpoint, Model, Dataset, and GCS Bucket) were deleted to ensure no costs were incurred.

---
## Model Performance & Results

The trained AutoML model demonstrated a solid ability to classify the severity of car damage.

**Confusion Matrix:**
The model performed best on `minor` damage but showed some confusion between `moderate` and `severe` cases.

![Confusion Matrix](Confusion%20matrix%20car%20damage%20project.png)

**Precision & Recall:**
The model achieved an overall **Average Precision of 58.3%** and a **Precision of 55.8%**.

![Precision and Recall Curve](precision%20and%20recall%20curve%20car%20damage%20project.png)

**Prediction Example:**
The deployed model correctly identified a test image from the `02-moderate` class with **89.9% confidence**.

---
## Technologies Used

-   **Cloud Platform:** Google Cloud Platform (GCP)
-   **Core Services:** Vertex AI, AutoML Vision, Google Cloud Storage
-   **Language:** Python
-   **Libraries:**
    -   `google-cloud-aiplatform` (Vertex AI SDK)
    -   `google-cloud-storage`
    -   `pandas`
-   **Environment:** Jupyter Notebook

---
## How to Run This Project

1.  **Prerequisites:** A Google Cloud Platform account with a project created and billing enabled. The `gcloud` CLI must be installed and authenticated.
2.  **Clone the repository:**
    ```bash
    git clone https://github.com/RedaElGadida/portfolio.git
    cd portfolio/Car-Damage-Vision

    ```
3.  **Install dependencies:**
    ```bash
    pip install pandas google-cloud-aiplatform google-cloud-storage
    ```
4.  **Run the notebook:** Open the `car-damage-analysis.ipynb` file in a Jupyter environment and run the cells sequentially, updating the `PROJECT_ID` and other configuration variables as needed.
