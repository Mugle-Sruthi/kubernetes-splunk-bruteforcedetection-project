# Kubernetes-Splunk-BruteForceDetection-Project

Flask-based Secure Login System with Suspicious Activity Detection using Kubernetes and Splunk

---

## Introduction
In the ever-evolving digital security landscape, brute force attacks remain a significant threat to cloud-native applications. This project, titled **"Kubernetes-Splunk-BruteForceDetection-Project"**, is designed to simulate and detect brute force login attempts in a secure, containerized environment using Kubernetes. By integrating a Flask-based secure login system with Splunk for real-time log analysis, the project aims to provide actionable insights into unauthorized access attempts.

This system supports user registration and login functionality while actively tracking suspicious behavior such as multiple failed login attempts. All events and logs are captured and forwarded to Splunk, where security analysts can visualize and respond to threats more effectively.

---

## Table of Contents
1. Overview
2. Features
3. Technologies Used
4. Project Structure
5. Prerequisites
6. Setup Instructions
7. Dockerization Details
8. Kubernetes Configuration
9. Splunk Integration
10. Conclusion
11. Contributing
12. License

---

## 1. Overview
This project includes a simple Flask application that simulates a login system deployed in a Kubernetes cluster. It captures login attempts, including failed attempts, and sends these logs to Splunk for further analysis. The goal is to emulate brute force attacks and understand how to detect and respond to them efficiently.

---

## 2. Features
- **Secure Login System**: Flask-based interface for user authentication
- **Suspicious Activity Detection**: Tracks multiple failed login attempts
- **Real-time Logging**: Sends logs to Splunk for monitoring
- **Kubernetes Deployment**: Ensures scalable and manageable deployment
- **Volume Mounting**: Shared volume for persistent logging

---

## 3. Technologies Used
- **Backend**: Python, Flask
- **Security Monitoring**: Splunk
- **Containerization**: Docker
- **Orchestration**: Kubernetes
- **Version Control**: GitHub

---

## 4. Project Structure
```
.
bruteforce-detection-app/
├── app.py                      # Main Flask application script
├── Dockerfile                 # Docker configuration file
├── .dockerignore              # Files/directories to ignore in Docker build
├── login_attempt.log          # Log file to track login attempts
├── requirements.txt           # Python dependencies
├── venvsruthi/                # Virtual environment folder (should be added to .dockerignore)
│
├── static/                    # Static files like CSS, JS, images
│   └── style.css              # Custom styling for the app UI
│
├── templates/                 # HTML templates for the Flask app
│   ├── create_user.html       # User registration page
│   ├── dashboard.html         # Dashboard showing login analytics or user status
│   └── index.html             # Login page (fake page to simulate attack)


---

## 5. Prerequisites
Ensure you have the following installed:
- Docker
- Kubernetes (AWS EC2 instance)
- Splunk instance (AWS ec2)
- Git

---

## 6. Setup Instructions
Clone the Repository:
```bash
git clone https://Mugle-Sruthi/kubernetes-splunk-bruteforce
cd kubernetes-splunk-bruteforce
```

Build the Docker Image:
```bash
docker build -t bruteforce-detection .
```

Deploy to Kubernetes:
```bash
kubectl apply -f bruteforce-detection.yaml
```

Access the Application:
Visit `http://<EC-2 publicIP>:<NodePort>` in your browser.

---

## 7. Dockerization Details
**Dockerfile**:
```dockerfile
FROM python:3.13-slim
WORKDIR /app
COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt
COPY . .
RUN mkdir -p /var/log/app && chmod -R 777 /var/log/app
CMD ["python", "app.py"]
```

---

## 8. Kubernetes Configuration
**deployment.yaml** contains both Deployment and Service definitions:
- **Deployment**: Runs 2 replicas, mounts a log volume, sets env variables
- **Service**: Exposes app via LoadBalancer (or NodePort)

---

## 9. Splunk Integration
- All login activities and suspicious events are logged to `/var/log/app`
- These logs can be forwarded to Splunk using a forwarder or webhook
- Dashboards can be created in Splunk to visualize brute force attempts

---

## 10. Conclusion
The **Kubernetes Brute Force Attack Simulation & Detection System** offers a secure and scalable platform to detect and respond to brute force attempts. By combining the flexibility of Flask, the orchestration of Kubernetes, and the powerful visualization of Splunk, this system empowers security teams to proactively monitor and respond to threats in real time. It acts as a training and simulation tool to refine security posture and incident response strategies.

---

## 11. Contributing
Contributions are welcome! Fork the repo, make your changes, and submit a pull request.

---

## 12. License
This project is licensed under the MIT License. See the LICENSE file for details.

