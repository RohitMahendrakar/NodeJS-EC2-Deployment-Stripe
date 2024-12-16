# NodeJS EC2 Deployment with Stripe Integration

This repository demonstrates how to deploy a Node.js application with Stripe payment integration on an EC2 instance. The application listens on port 3000 and serves the application to the world through your EC2 server. 

## Prerequisites

Before proceeding with the setup, ensure you have:

- An AWS EC2 instance (running Amazon Linux 2 or a similar OS).
- Stripe API keys (both public and secret keys).
- A GitHub account to clone the repository.

## Setting Up Locally

### 1. Clone the Repository
Clone this repository to your local machine:
```bash
git clone https://github.com/RohitMahendrakar/NodeJS-EC2-Deployment-Stripe.git
cd NodeJS-EC2-Deployment-Stripe
```

### 2. Create `.env` File

Create a `.env` file to store your environment variables (do not commit this file to Git):

```bash
touch .env
```

Add the following content to your `.env` file:

```env
DOMAIN=""
PORT=3000
STATIC_DIR="./client"

PUBLISHABLE_KEY="your_stripe_publishable_key"
SECRET_KEY="your_stripe_secret_key"
```

Replace `your_stripe_publishable_key` and `your_stripe_secret_key` with the keys from your Stripe account.

### 3. Install Dependencies

Run the following command to install the required Node.js dependencies:

```bash
npm install
```

### 4. Start the Application

Once the dependencies are installed, start the application:

```bash
npm run start
```

This will start the application on `http://localhost:3000`. Open the URL in your browser to check if it works locally.

## Setting Up on EC2

### 1. Connect to your EC2 instance

SSH into your EC2 instance:

```bash
ssh -i your-key.pem ec2-user@your-ec2-public-ip
```

### 2. Install Required Software

Update your EC2 instance and install Git and npm:

```bash
sudo yum update -y
sudo yum install git -y
sudo yum install npm -y
```

### 3. Clone the Repository to EC2

Clone your repository onto the EC2 instance:

```bash
git clone https://github.com/RohitMahendrakar/NodeJS-EC2-Deployment-Stripe.git
cd NodeJS-EC2-Deployment-Stripe
```

### 4. Install Dependencies

Run the following command on EC2 to install dependencies:

```bash
npm install
```

### 5. Open Port 3000 in the EC2 Security Group

To make your application accessible from the outside world, open port 3000 in the EC2 security group.

- Go to the EC2 Dashboard.
- Select **Security Groups** under **Network & Security**.
- Select your security group.
- Click on **Edit inbound rules**.
- Add a new rule for **Custom TCP** with port `3000` and source `0.0.0.0/0` (for global access).

### 6. Start the Application on EC2

Start your application on the EC2 instance:

```bash
npm run start
```

### 7. Verify the Application

Once the application is running, you can access it by visiting the following URL (replace `your-ec2-public-ip` with your EC2 instance's public IP):

```bash
http://your-ec2-public-ip:3000
```

### 8. Stripe Integration

To integrate with Stripe, you can log in to your Stripe account, navigate to **Settings** -> **API Keys** and generate your **Publishable Key** and **Secret Key**. Insert these keys in the `.env` file.

## Conclusion

This setup allows you to deploy a Node.js application with Stripe integration on an EC2 instance, making it publicly accessible on port 3000. Be sure to keep your `.env` file safe and never expose your secret keys publicly.
```

### Key Points:
- **Repository Name**: `NodeJS-EC2-Deployment-Stripe`
- **Features**: Instructions for local development and EC2 deployment, environment setup for Stripe, and port configuration for EC2.
  
This `README.md` should help you get started with the deployment process. Let me know if you'd like any additional changes!
