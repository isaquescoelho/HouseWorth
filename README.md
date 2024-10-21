# HouseWorth

## Overview

HouseWorth  is an end-to-end automated pipeline for building, training, deploying, and monitoring machine learning models. The project focuses on automating the machine learning lifecycle using modern MLOps techniques, making it ideal for dynamic environments like real estate pricing where models need constant updating.

### Features
- **Data Pipeline**: Automates data collection, cleaning, and preprocessing.
- **Model Training**: Trains models based on the latest data and stores versions with unique IDs.
- **Model Deployment**: Uses Docker and Kubernetes to containerize and deploy the model.
- **CI/CD Integration**: Implements CI/CD pipelines for automated model retraining and deployment on code or data changes.
- **Monitoring and Logging**: Tracks model performance in real time, collects logs, and triggers alerts when anomalies are detected.

### Tech Stack
- **Programming Language**: Python
- **Machine Learning Framework**: TensorFlow or PyTorch
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **CI/CD**: GitHub Actions
- **Cloud Services**: AWS (EC2, ECR, EKS)
- **Monitoring**: Prometheus, Grafana

### Architecture

1. **Data Ingestion and Preprocessing**: An ETL process to collect and clean data, making it ready for training.
2. **Model Training**: A Python script that trains a model with the cleaned data, using TensorFlow/PyTorch.
3. **Model Versioning**: The trained model is stored with a version number for easy rollback and tracking.
4. **Deployment**: Docker is used to containerize the model, and Kubernetes manages its deployment in a scalable environment.
5. **Monitoring and Alerting**: Prometheus collects metrics, and Grafana visualizes them. Alerts are set up for anomalies or performance drops.

### Setup and Installation

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/isaquescelho/HouseWorth.git
   ```
2. **Build Docker Image**:
   ```bash
   docker build -t automl-deploy .
   ```
3. **Deploy on Kubernetes**:
   ```bash
   kubectl apply -f kubernetes/deployment.yaml
   ```
4. **Configure CI/CD**: Update the `.github/workflows/main.yml` file to match your repository and environment.
5. **Set Up Monitoring**:
   - Install Prometheus and Grafana using Helm:
     ```bash
     helm install prometheus stable/prometheus
     helm install grafana stable/grafana
     ```

### How to Use

1. **Data Preparation**:
   - Place your dataset in the `/data` directory.
   - The pipeline automatically preprocesses and cleans data on execution.
2. **Training the Model**:
   - Run the training script:
     ```bash
     python train.py
     ```
   - The trained model will be saved in the `/models` directory.
3. **Deployment**:
   - Deploy the latest model using:
     ```bash
     kubectl apply -f kubernetes/deployment.yaml
     ```
4. **Monitoring**:
   - Access Grafana at `http://<your-server-ip>:3000` to view model performance and logs.

### Contributing

Feel free to fork the repository and submit pull requests. We welcome contributions that add new features or improve the existing pipeline!

### License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
