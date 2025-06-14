<h1>☕ Dynamic Café Website – AWS Deployment Project</h1>

This project showcases the deployment of a dynamic website for a local café that allows customers to place **online orders**. The application is hosted on **Amazon EC2**, with secure secret management using **AWS Secrets Manager**, and infrastructure deployed across **multiple AWS Regions** to represent development and production environments.

<h2>🚀 Project Overview</h2>

- ✅ Deploy a custom web app that simulates a café ordering system
- ✅ Use **Cloud9** IDE for development directly on an EC2 instance
- ✅ Secure credentials with **AWS Secrets Manager**
- ✅ Create an **Amazon Machine Image (AMI)** from the Dev instance
- ✅ Launch a **production copy** of the app in another region (Oregon)

<h3>At the end of this project, your architecture should look like the following example:</h3>
<br/>
<img src="aws ordering website.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h2>🛠️ Services & Tools Used</h2>

| AWS Service         | Purpose                                           |
|---------------------|---------------------------------------------------|
| EC2                 | Hosting web app (Dev + Prod)                      |
| Cloud9              | Cloud-based development environment               |
| Secrets Manager     | Securely manage database credentials              |
| Amazon Machine Image (AMI) | Reuse configured server setup across regions |
| IAM                 | Permissions to access Secrets Manager securely    |
| Security Groups     | Control inbound traffic to web servers            |

---

User Browser ───▶ EC2 (Dev Region) ──┐
├─▶ AMI ──▶ EC2 (Prod Region)
Secrets Manager ◀───────────────────┘

<h3>⚙️ Setup Instructions</h3>

### 1. Set Up Cloud9 Dev Environment
- Launch Cloud9 in the `us-east-1` region
- Use a t3.micro EC2 instance with Amazon Linux 2
- Update system and install Apache or PHP as needed

### 2. Install Application + Secrets Manager
- Create a simple PHP app (or your own)
- Use AWS SDK to pull secrets from **Secrets Manager**
- Store credentials (e.g., `db_password`) securely

### 3. Create & Copy AMI
- Create an AMI from the Dev instance
- Copy the AMI to `us-west-2` (Oregon)

### 4. Deploy Production Instance
- Launch a new EC2 instance in Oregon using the copied AMI
- Confirm HTTP access and test web app functionality

---

## 🔐 Example: Retrieving Secrets in PHP

php
$client = new SecretsManagerClient([...]);
$result = $client->getSecretValue(['SecretId' => 'CafeAppDBSecret']);
$secret = json_decode($result['SecretString'], true);
echo $secret['db_password'];

<h2>✅ Outcome</h2>
By the end of this project:

The Dev environment hosts and tests the app in one region

An AMI captures the working environment

A second Prod instance runs the same app in a different AWS Region

Secrets are securely managed using AWS-native tools

<h2>📂 Future Improvements</h2>

Add RDS database integration

Enable HTTPS with ACM + Load Balancer

CI/CD pipeline with CodePipeline + CodeDeploy

Add authentication with Amazon Cognito

<h4>📄 License</h4>
This project is open-sourced for educational and demonstration purposes. Feel free to fork and customize it for your own use.

<h1>🙌 Author</h1>
Covenant Onwukwe
AWS Solutions Architect
Lagos, Nigeria 🇳🇬


