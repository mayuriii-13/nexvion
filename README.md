\# 🛍️ Nexvion — E-Commerce Website



Nexvion is a static e-commerce website demo built with HTML, CSS, and JavaScript, containerized with Docker, hosted using Amazon S3, and automated with GitHub Actions CI/CD.



The project demonstrates practical \*\*AWS, Docker, Git, GitHub, IAM, OIDC, and CI/CD\*\* concepts.



\---



\## 🚀 Live Architecture



```text

Developer

&#x20;  │

&#x20;  │ git push

&#x20;  ▼

GitHub Repository

&#x20;  │

&#x20;  ▼

GitHub Actions

&#x20;  │

&#x20;  │ OIDC authentication

&#x20;  ▼

AWS IAM Role

&#x20;  │

&#x20;  │ S3 permissions

&#x20;  ▼

Amazon S3

&#x20;  │

&#x20;  ▼

Nexvion Website Files



CloudFront was used during an earlier deployment phase but is currently disabled to avoid unnecessary ongoing costs.



✨ Features

🛒 Shopping

\- Product catalogue with 12 products

\- Product search

\- Category filtering

\- Price filtering

\- Stock filtering

\- Product sorting

\- Shopping cart

\- Cart quantity controls

👤 Account

\- Login

\- Registration

\- Logout

\- LocalStorage-based account persistence

\- LocalStorage-based cart persistence

💳 Checkout Demo

\- Separate payment page

\- Card number validation

\- CVV validation

\- Expiry date validation

\- UPI validation

\- Cash on Delivery option

\- Order confirmation

Important: Authentication and payment functionality are frontend demo features using browser LocalStorage. No real payment gateway or production authentication service is implemented.



🛠️ Technologies Used

Frontend

\- HTML5

\- CSS3

\- JavaScript

\- Browser LocalStorage

DevOps / Cloud

\- Git

\- GitHub

\- GitHub Actions

\- Docker

\- Docker Hub

\- Amazon S3

\- AWS IAM

\- GitHub OIDC

🐳 Docker

The application is containerized using Nginx.

Dockerfile

The Docker image uses:

FROM nginx:alpine



Website files are copied into the Nginx web root.

Build Docker Image

docker build -t nexvion:1.0 .



Run Locally

docker run -d -p 8080:80 --name nexvion-container nexvion:1.0



Open:

http://localhost:8080



Docker Hub

The Docker image is published to Docker Hub:

mayurii13/nexvion

☁️ AWS Deployment

The website files are hosted in an Amazon S3 bucket.

AWS Services Used

\- Amazon S3

\- AWS IAM

\- IAM OIDC Identity Provider

\- GitHub Actions

The S3 bucket is configured with controlled access rather than making the bucket publicly writable.

🔄 CI/CD Pipeline

Nexvion uses GitHub Actions to automatically deploy website changes to Amazon S3.

Deployment Flow

Git Push

&#x20;  ↓

GitHub Actions

&#x20;  ↓

Checkout Repository

&#x20;  ↓

AWS OIDC Authentication

&#x20;  ↓

Assume IAM Deployment Role

&#x20;  ↓

Upload Website Files

&#x20;  ↓

Amazon S3



Whenever changes are pushed to the main branch, the GitHub Actions workflow runs automatically.

🔐 AWS OIDC Authentication

The CI/CD pipeline does not use long-lived AWS access keys.

Instead, GitHub Actions uses OpenID Connect (OIDC) to obtain temporary AWS credentials.

The IAM trust policy restricts the deployment role to the Nexvion repository and main branch.

This provides a more secure authentication model for GitHub-to-AWS deployments.

🔑 IAM Least Privilege

The GitHub Actions deployment role is dedicated to Nexvion.

Its S3 permissions are limited to the Nexvion bucket and required deployment actions.

This follows the AWS least-privilege principle instead of granting broad administrator permissions.

📁 Project Structure

Nexvion-main/

│

├── index.html

├── products.html

├── payment.html

│

├── style.css

├── products.css

├── payment.css

│

├── script.js

├── payment.js

│

├── logo.png

│

├── Dockerfile

├── README.md

├── README.txt

├── .gitignore

│

└── .github/

&#x20;   └── workflows/

&#x20;       └── deploy.yml



🔒 Security Notes

This project is a learning and portfolio demonstration.

The following are intentionally not implemented as production systems:

\- Real payment processing

\- Production authentication

\- Backend API

\- Real user database

\- Secure server-side sessions

A production e-commerce application would require a backend, secure authentication, database, HTTPS, server-side validation, and a certified payment gateway.

🎯 DevOps Learning Outcomes

Through this project, I practiced:

\- Git version control

\- GitHub repository management

\- Docker containerization

\- Docker image creation

\- Docker Hub publishing

\- Amazon S3 deployment

\- AWS IAM roles

\- IAM OIDC federation

\- GitHub Actions

\- CI/CD automation

\- Least-privilege access

\- Cloud deployment architecture

👩‍💻 Author

Mayuri Ambare

B.Tech — Electronics \& Telecommunication Engineering

Cloud \& DevOps Engineer | AWS | Docker | Kubernetes | Terraform | Linux

GitHub: mayuriii-13

