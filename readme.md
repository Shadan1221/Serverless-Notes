# Serverless Notes Application

## 📌 Project Overview
The **Serverless Notes Application** is a cloud-based application that allows users to create and retrieve notes using AWS serverless services.  
It is built with a **fully managed backend** powered by **API Gateway, Lambda, DynamoDB, and SNS**, while the frontend is hosted on **Amazon S3** as a static website.

This project demonstrates the use of serverless computing to build a scalable, cost-efficient, and highly available application without managing any servers.

---

## 🏗️ Architecture

![Architecture Diagram](./architecture.png) <!-- Replace with actual diagram image -->

### Workflow:
1. **Frontend (Amazon S3)**
   - Hosts the static website (`index.html`, CSS, and JavaScript).
   - Provides the user interface to add and view notes.

2. **API Gateway**
   - Acts as the entry point for the application.
   - Exposes two REST API endpoints:
     - `POST /create_note` → Add a new note
     - `GET /get_notes` → Fetch all notes

3. **AWS Lambda**
   - Contains the serverless logic.
   - `create_note` function → stores a new note into DynamoDB and optionally publishes a message to SNS.
   - `get_notes` function → retrieves all notes from DynamoDB and returns them as JSON.

4. **Amazon DynamoDB**
   - NoSQL database to store notes.
   - Each note has:
     - `noteId` (UUID - primary key)
     - `text` (content of the note)
     - `createdAt` (timestamp)

5. **Amazon SNS (Optional)**
   - Used for sending notifications whenever a new note is created.

---

## ⚙️ Technologies Used
- **Frontend**: HTML, CSS, JavaScript
- **Backend**: AWS Lambda (Python)
- **Database**: DynamoDB
- **API Gateway**: REST API
- **Storage**: Amazon S3 (Static Website Hosting)
- **Notifications**: SNS
- **IAM**: Custom policy for Lambda access (DynamoDB, CloudWatch Logs, SNS)

---

## 📂 Project Structure
├── index.html # Frontend (UI)
├── lambda/
│ ├── create_note/ # Lambda function for creating notes
│ └── get_notes/ # Lambda function for retrieving notes
├── architecture.png # Architecture Diagram
└── README.md # Documentation