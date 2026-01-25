# EC2 GitHub Actions Deploy 🚀

Automated deployment to AWS EC2 using GitHub Actions.

## 🌐 Live Website

**URL:** [http://13.62.128.44](http://13.62.128.44)

## 📁 Project Structure

```
├── index.html                    # Main website file
├── README.md                     # Project documentation
└── .github/
    └── workflows/
        └── deploy.yml            # GitHub Actions workflow
```

## ⚙️ How It Works

1. Push code to the `main` branch
2. GitHub Actions automatically triggers
3. Connects to EC2 via SSH
4. Pulls the latest code from the repository

## 🔧 Setup Requirements

### GitHub Secrets

Configure these secrets in your repository (Settings → Secrets → Actions):

| Secret Name | Description |
|-------------|-------------|
| `EC2_HOST` | EC2 public IP address |
| `EC2_USERNAME` | SSH username (e.g., `ubuntu`) |
| `EC2_SSH_KEY` | Private key (.pem file contents) |

### EC2 Security Group

Ensure these inbound rules are configured:

| Type | Port | Source |
|------|------|--------|
| SSH | 22 | 0.0.0.0/0 |
| HTTP | 80 | 0.0.0.0/0 |

### EC2 Server Setup

```bash
sudo apt update
sudo apt install git nginx -y
cd /var/www/html
sudo git clone https://github.com/YasinAsif/ec2-github-actions-deploy.git .
sudo chown -R ubuntu:ubuntu /var/www/html
```

## 🚀 Deployment

Simply push to the `main` branch:

```bash
git add .
git commit -m "Your commit message"
git push origin main
```

The workflow will automatically deploy your changes to EC2.

## 📝 License

MIT License
