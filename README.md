# Dockerized DynamoDB Form App
A simple Node.js web application that allows users to submit a form with Name, Email, Phone.
The data is securely stored in AWS DynamoDB, and the app runs in a Docker container on an EC2 instance using IAM roles — no AWS keys needed.

# Features:-

-> Fully Dockerized Node.js app

-> Frontend form with file upload support

-> Stores submissions in DynamoDB table

-> Uses EC2 IAM Role for secure AWS access

-> Easy to deploy on EC2 using Docker

# Technologies Used:-

-> Node.js (Express backend)

-> HTML, CSS, JavaScript (Frontend)

-> AWS DynamoDB (Data storage)

-> Docker (Containerization)

-> AWS IAM Role (Secure credentials)

# Project Structure:-
.
├── Dockerfile
├── package.json
├── server.js
├── public
    ├── index.html
    ├── style.css
    └── script.js


# Setup Instructions:-

1. Prepare DynamoDB Table

   ->Table name: Users

   ->Partition key: id (String)

   ->Other attributes (name, email, phone, file_path) are optional

2. Docker Hub Image

   ->Build and push your image (or use the existing one):
      docker build -t yourdockerhubusername/myapp-dynamodb .
      docker push yourdockerhubusername/myapp-dynamodb:latest

3. Run on EC2

   ->Ensure your EC2 has an IAM role with DynamoDB access.
     Run the container:
     docker run -d -p 80:3000 --name node-dynamo-app -e AWS_REGION=eu-north-1 yourdockerhubusername/myapp-dynamodb:latest

   ->Open in browser:
     http://YOUR_EC2_PUBLIC_IP/

   ->Submit the form — data will be saved to DynamoDB.

ScreenShot:-
------------

                    ---image--




# Notes:-

-> No AWS keys are needed if EC2 has an IAM Role

-> Uploaded files are stored inside the container (uploads/ folder)

-> You can map a volume to persist uploads outside the container
