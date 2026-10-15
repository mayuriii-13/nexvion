# 🛍️ Nexvion — E-Commerce Website

Nexvion is a static e-commerce website demo built with **HTML, CSS, and JavaScript**, containerized with **Docker**, hosted using **Amazon S3**, and automated with **GitHub Actions CI/CD**.

The project demonstrates practical **AWS, Docker, Git, GitHub, IAM, OIDC, and CI/CD** concepts.

---

## 🚀 Architecture

```text
Developer
   │
   │ git push
   ▼
GitHub Repository
   │
   ▼
GitHub Actions
   │
   │ OIDC authentication
   ▼
AWS IAM Role
   │
   │ S3 permissions
   ▼
Amazon S3
   │
   ▼
Nexvion Website
```

> CloudFront was used during an earlier deployment phase but is currently disabled to avoid unnecessary ongoing costs.

---

## ✨ Features

### 🛒 Shopping

- Product catalogue with 12 products
- Product search
- Category filtering
- Price filtering
- Stock filtering
- Product sorting
- Shopping cart
- Cart quantity controls

### 👤 Account

- Login
- Registration
- Logout
- LocalStorage-based account persistence
- LocalStorage-based cart persistence

### 💳 Checkout Demo

- Separate payment page
- Card number validation
- CVV validation
- Expiry date validation
- UPI validation
- Cash on Delivery option
- Order confirmation

> **Important:** Authentication and payment functionality are frontend demo features using browser LocalStorage. No real payment gateway or production authentication service is implemented.

---

## 🛠️ Technologies Used

### Frontend

- HTML5
- CSS3
- JavaScript
- Browser LocalStorage

### DevOps / Cloud

- Git
- GitHub
- GitHub Actions
- Docker
- Docker Hub
- Amazon S3
- AWS IAM
- GitHub OIDC

---

## 🐳 Docker

The application is containerized using **Nginx**.

### Build Docker Image

```bash
docker build -t nexvion:1.0 .
```

### Run Locally

```bash
docker run -d -p 8080:80 --name nexvion-container nexvion:1.0
```

Open:

```text
http://localhost:8080
```

### Docker Hub

The Docker image is published on Docker Hub:

**mayurii13/nexvion**

---

## ☁️ AWS Deployment

The Nexvion website files are hosted in an **Amazon S3** bucket.

### AWS Services Used

- Amazon S3
- AWS IAM
- IAM OIDC Identity Provider
- GitHub Actions

The S3 bucket uses controlled access rather than allowing public write access.

---

## 🔄 CI/CD Pipeline

Nexvion uses **GitHub Actions** to automatically deploy website changes to Amazon S3.

### Deployment Flow

```text
Git Push
   ↓
GitHub Actions
   ↓
Checkout Repository
   ↓
AWS OIDC Authentication
   ↓
Assume IAM Deployment Role
   ↓
Upload Website Files
   ↓
Amazon S3
```

Whenever changes are pushed to the `main` branch, the GitHub Actions workflow runs automatically.

---

## 🔐 AWS OIDC Authentication

The CI/CD pipeline does **not** use long-lived AWS access keys.

Instead, GitHub Actions uses **OpenID Connect (OIDC)** to authenticate with AWS and obtain temporary credentials.

The IAM trust policy restricts the deployment role to the Nexvion GitHub repository and `main` branch.

This provides a more secure authentication model for GitHub-to-AWS deployments.

---

## 🔑 IAM Least Privilege

The GitHub Actions deployment role is dedicated to Nexvion.

Its S3 permissions are limited to the Nexvion bucket and the actions required for deployment.

This follows the AWS **least-privilege** principle instead of granting broad administrator permissions.

---

## 📁 Project Structure

```text
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
    └── workflows/
        └── deploy.yml
```

---

## 🔒 Security & Production Notes

This project is a **learning and portfolio demonstration**.

The following are not implemented as production systems:

- Real payment processing
- Production authentication
- Backend API
- Real user database
- Secure server-side sessions

A production e-commerce application would require:

- Backend services
- Secure authentication
- Database
- HTTPS
- Server-side validation
- Secure session management
- A certified payment gateway

---

## 🎯 DevOps Learning Outcomes

Through this project, I practiced:

- Git version control
- GitHub repository management
- Docker containerization
- Docker image creation
- Docker Hub publishing
- Amazon S3 deployment
- AWS IAM roles
- IAM OIDC federation
- GitHub Actions
- CI/CD automation
- Least-privilege access
- Cloud deployment architecture

---

## 👩‍💻 Author

**Mayuri Ambare**

B.Tech — Electronics & Telecommunication Engineering

**Cloud & DevOps Engineer | AWS | Docker | Kubernetes | Terraform | Linux**

GitHub: [mayuriii-13](https://github.com/mayuriii-13)
