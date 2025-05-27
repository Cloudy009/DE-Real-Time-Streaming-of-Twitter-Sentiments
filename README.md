# 🐦 Twitter Sentiment Analysis – Real-Time Streaming Project

This project implements a **real-time data pipeline** to perform **sentiment analysis on Twitter data**, using a full modern data stack deployed via **Docker** on an **AWS EC2 instance**. The results are visualized using **Plotly Dash**.

## 📌 Project Overview

The goal of this project is to build an end-to-end pipeline to:
- Collect real-time tweets using the Twitter API.
- Process and clean tweets using Apache NiFi, Apache Kafka, and Apache Spark.
- Perform sentiment analysis using a supervised ML model (Logistic Regression + TF-IDF).
- Store processed data in MongoDB.
- Visualize results in a web dashboard (Plotly + Dash).

## 🛠️ Tech Stack

| Component        | Version   | Purpose                          |
|------------------|-----------|----------------------------------|
| Docker           | 3.0.0     | Containerization                 |
| Apache NiFi      | 1.3.2     | Data ingestion                   |
| Apache Kafka     | 2.8.0     | Stream processing                |
| Apache Spark     | 3.1.1     | Data transformation & ML         |
| MongoDB          | 4.4.5     | NoSQL storage                    |
| Dash             | 1.20.0    | Web dashboard                    |
| Jupyter Lab      | latest    | Experimentation & development    |

## ⚙️ System Requirements

- OS: Ubuntu 16.04 (recommended)
- AWS EC2 Instance: `t2.xLarge` with **32 GB RAM**
- External terminal: For Windows (e.g. PuTTY), SSH for Mac/Linux

## 📁 Folder Structure

├── docker-compose.yml # Docker container definitions
├── Presentation.ipynb # Project summary
├── schemagenerator.ipynb # Data schema handling
├── sentimentanalyzer.ipynb # ML pipeline and sentiment classification
├── streamlistener.ipynb # Streaming tweet listener
├── sentimentvisualizer.ipynb # Dash-based data visualization


## 🧠 ML Pipeline Overview

- Data Collection: Twitter API via NiFi
- Preprocessing: Tokenization, stopword removal, TF-IDF
- Model: Logistic Regression
- Evaluation: Binary classification evaluator
- Model persistence: Save for real-time inference

## 🔄 Data Pipeline Flow

1. **Extraction**: NiFi captures Twitter stream via API.
2. **Streaming**: Tweets published to Kafka topics.
3. **Transformation**: Spark reads data from Kafka, applies sentiment analysis.
4. **Load**: Data is written to MongoDB.
5. **Visualization**: Dash dashboard displays real-time sentiment data.

---------------------------------------------------------------------------------
## 🚀 How to Run the Project

### 1. Launch EC2 instance
- Use Ubuntu 16.04 AMI with at least 32 GB RAM.
- SSH into your instance.

### 2. Install Docker & run containers
sudo apt-get update
sudo apt install docker.io docker-compose
docker-compose up -d

### 3. Open Jupyter Lab
jupyter notebook --ip=0.0.0.0 --no-browser

### 4. Access NiFi UI
Visit http://<EC2_IP>:8080/nifi

### 5. View Dashboard
Open: http://<EC2_IP>:8050 for Dash visualization.

## 💡 Notes
- NiFi Errors: If you face image issues, try changing the Docker image to:
    apache/nifi:1.14.0 or apache/nifi:1.12.0 or pavansrivathsa/nifi

- Edit Jupyter Files in Docker:
    docker exec -it <container_id_or_name> bash
    cd /home/jupyter/
    nano <file_name>.ipynb

## 📊 Sample Visuals
Includes:
    Real-time scatter plots of tweet sentiments
    Data tables for tweet details and sentiment categories

## 📝 License
This project is for educational purposes only.
"# DE-Real-Time-Streaming-of-Twitter-Sentiments" 
