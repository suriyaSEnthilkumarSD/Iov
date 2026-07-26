# Iov
AI-powered Open-Set Intrusion Detection System for Internet of Vehicles (IoV) using Variational Autoencoder (VAE), OpenMax, and Continual Learning with an interactive Streamlit web interface for real-time cyber attack detection and novel attack recognition.

# AI-Based Open-Set Intrusion Detection System for Novel Attack Detection in Internet of Vehicles (IoV)

##  Overview

Modern Intrusion Detection Systems (IDS) are primarily designed to detect only attack types encountered during training. However, cyber threats continuously evolve, making conventional closed-set detection approaches ineffective against previously unseen attacks. This limitation is especially critical in the **Internet of Vehicles (IoV)**, where connected vehicles exchange large volumes of sensitive data and require intelligent, adaptive security mechanisms.

This project presents an **AI-Based Open-Set Intrusion Detection System (IDS)** capable of detecting **known attacks, identifying novel (unknown) attacks, and continuously learning newly discovered attack classes**. The proposed system combines **Variational Autoencoder (VAE)** for anomaly detection, **Temporal CNN with OpenMax** for open-set recognition, and **Continual Learning** to incrementally learn emerging attacks without retraining the entire model.

An interactive **Streamlit web application** enables users to upload network traffic data, perform real-time intrusion analysis, and visualize detection results through an intuitive interface.

---

# Problem Statement

Traditional machine learning and deep learning-based Intrusion Detection Systems assume that every incoming attack belongs to one of the attack classes observed during training. In real-world environments, attackers continuously develop new attack techniques that were never seen during model training.

This project addresses the following challenges:

* Detection of malicious network traffic.
* Identification of previously unseen (novel) attacks.
* Accurate classification of known attack types.
* Incremental learning of newly discovered attacks.
* Reduction of catastrophic forgetting during model updates.

---

#  Proposed Solution

The proposed IDS follows a **multi-stage AI pipeline** consisting of three major components:

1. Variational Autoencoder (VAE)
2. Temporal CNN with OpenMax
3. Continual Learning

Together, these components provide a robust framework capable of detecting both known and emerging cyber threats while continuously improving over time.

---

#  System Architecture
# <img width="1600" height="728" alt="14cf2896-5bb9-4965-af41-e3b2dec22388" src="https://github.com/user-attachments/assets/b9e7ed7c-9e0d-4965-b9ce-7ae51936b270" />




```text
                     Network Traffic
                            │
                            ▼
                 Data Preprocessing
                            │
                            ▼
       Stage 1 : Variational Autoencoder (VAE)
             (Benign vs Attack Detection)
                            │
          ┌─────────────────┴─────────────────┐
          │                                   │
       Benign                            Attack
          │                                   │
          ▼                                   ▼
                                Stage 2 : Temporal CNN
                             Deep Feature Extraction
                                        │
                                        ▼
                                    OpenMax
                       (Known vs Novel Attack Detection)
                       ┌──────────────────┴──────────────────┐
                       │                                     │
                 Known Attack                         Novel Attack
                       │                                     │
                       │                           Store Novel Samples
                       │                                     │
                       └───────────────┬─────────────────────┘
                                       │
                                       ▼
                         Continual Learning Module
              (Known Attacks + Newly Discovered Attacks)
                                       │
                                       ▼
                          Updated Intelligent IDS Model
```

---

#  Methodology

## Stage 1 – Variational Autoencoder (VAE)

The first stage focuses on anomaly detection.

A Variational Autoencoder (VAE) is trained exclusively using benign network traffic to learn normal communication patterns within IoV networks.

During inference:

* Incoming network traffic is reconstructed by the VAE.
* Reconstruction error is calculated.
* Low reconstruction error indicates normal traffic.
* High reconstruction error indicates suspicious traffic and is forwarded to the next stage.

This stage effectively separates normal network traffic from potentially malicious traffic.

---

## Stage 2 – Temporal CNN with OpenMax

Traffic identified as malicious is processed by a Temporal Convolutional Neural Network (Temporal CNN).

The Temporal CNN extracts deep temporal representations of attack traffic, which are then analyzed using the OpenMax algorithm.

OpenMax performs Open-Set Recognition by:

* Measuring similarity between incoming traffic and known attack distributions.
* Rejecting unfamiliar attack patterns.
* Classifying attacks as either:

  * Known Attack
  * Novel Attack

Unlike conventional classifiers, OpenMax avoids forcing unknown attacks into existing attack categories.

---

## Stage 3 – Continual Learning

Novel attacks identified during the OpenMax stage are stored separately.

These newly discovered attacks are later combined with the existing known attack dataset to create an expanded training dataset.

The Continual Learning model is then trained on this combined dataset, enabling the IDS to:

* Learn new attack classes.
* Preserve knowledge of previously learned attacks.
* Reduce catastrophic forgetting.
* Continuously improve detection capability as new threats emerge.

This enables the IDS to evolve over time instead of remaining static after deployment.

---

#  Streamlit Web Interface

An interactive Streamlit web application was developed to simplify the usage of the Intrusion Detection System.

### Features

* Upload network traffic dataset
* Perform real-time intrusion detection
* Detect benign and malicious traffic
* Identify known and novel attacks
* Display final attack prediction
* Interactive and user-friendly interface

---

#  Dataset

The project utilizes network traffic datasets derived from the **CICIDS2017** dataset.

The datasets contain:

* Benign Traffic
* DoS Attacks
* Web Attacks
* Known Attack Classes
* Novel Attack Classes

The data undergoes several preprocessing steps before training.

---

#  Data Preprocessing

The preprocessing pipeline includes:

* Missing value handling
* Feature selection
* Label encoding
* One-hot encoding
* Feature normalization
* Data scaling
* Dataset balancing
* Sequence preparation for Temporal CNN

---

#  Technologies Used

### Programming Language

* Python

### Deep Learning

* TensorFlow
* Keras

### Machine Learning

* Scikit-learn

### Data Processing

* Pandas
* NumPy
* SciPy

### Web Application

* Streamlit

### Model Components

* Variational Autoencoder (VAE)
* Temporal CNN
* OpenMax
* Continual Learning

### Dataset

* CICIDS2017

---

#  Key Features

* Multi-stage AI-based Intrusion Detection System
* Deep Learning-based anomaly detection
* Open-Set Recognition for unknown attacks
* Temporal CNN feature extraction
* Continual Learning for adaptive attack classification
* Interactive Streamlit web application
* Real-time prediction pipeline
* Modular architecture for future enhancements

---

#  Complete Workflow

```text
Network Traffic
        │
        ▼
Data Preprocessing
        │
        ▼
Variational Autoencoder
        │
        ▼
Benign / Attack Detection
        │
        ▼
Temporal CNN Feature Extraction
        │
        ▼
OpenMax
        │
        ▼
Known Attack / Novel Attack
        │
        ▼
Store Novel Samples
        │
        ▼
Combine with Existing Attack Dataset
        │
        ▼
Continual Learning
        │
        ▼
Updated IDS Model
        │
        ▼
Final Prediction
```

---

#  Results

The proposed system successfully:

* Detects malicious network traffic using anomaly detection.
* Distinguishes known attacks from previously unseen attacks.
* Stores novel attacks for future learning.
* Incrementally learns newly discovered attack classes using Continual Learning.
* Improves the adaptability of the Intrusion Detection System against evolving cyber threats.


---

#  Future Enhancements

* Live packet capture integration
* Real-time IoV traffic monitoring
* Explainable AI (XAI) for attack interpretation
* Cloud deployment
* REST API integration
* Docker containerization
* CI/CD deployment pipeline
* Federated continual learning for distributed IoV environments

---

# Author

**Suriya Senthilkumar**

B.E. Computer Science and Engineering

College of Engineering Guindy, Anna University

---


 License

This project is developed for academic and research purposes. It demonstrates the application of deep learning, open-set recognition, and continual learning techniques for intelligent intrusion detection in Internet of Vehicles (IoV) environments.
