# QR Code Generator

A **Spring Boot** application that generates **QR Codes** and stores them in an **AWS S3 bucket**.
The project is fully containerized with **Docker** for easy local execution and deployment.

**Credits:** Fernanda Kipper Dev

---

## 🚀 Overview

This application:

* Generates QR Codes from text or URLs
* Uploads the generated image to **Amazon S3**
* Returns a URL to access the QR Code

All configuration is handled via environment variables.

---

## 🛠️ Technologies

* Java
* Spring Boot
* Docker
* AWS S3
* Maven

---

## 📦 Prerequisites

* Docker
* AWS account with an S3 bucket
* AWS credentials with S3 write permission

> ⚠️ Check [here](https://www.kipperdev.com.br/blog/guia-completo-para-configurar-aws-no-intellij/) how to setup AWS credentials.

---

## ▶️ Running the application

### 1️⃣ Clone the repository

### 2️⃣ Create a `.env` file

```env
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_REGION=us-east-1
AWS_S3_BUCKET=your_bucket_name
```

> ⚠️ Do not commit this file.

### 3️⃣ Build and run with Docker

```bash
docker build -t qrcode-generator:latest .
docker run --env-file .env -p 8080:8080 qrcode-generator:latest
```

---

## 🌐 Testing the API

You can test the application using **Postman**, **Insomnia**, or **cURL**.

### Endpoint

```
POST http://localhost:8080/qrcode
```

### Request body

```json
{
  "text": "https://fernandakipper.com/links"
}
```

### Result

* A QR Code is generated and uploaded to **AWS S3**
* The API returns a **URL**

![img01](assets/asset01.png)

* Opening this URL in your browser displays the QR Code image

![img01](assets/asset02.png)

### cURL example

```bash
curl -X POST http://localhost:8080/qrcode \
  -H "Content-Type: application/json" \
  -d '{"text":"https://fernandakipper.com/links"}'
```

---

## 📌 Notes

* Intended for learning and demonstration purposes
* Keep AWS credentials secure
* For production, prefer AWS IAM roles over static credentials
