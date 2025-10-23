# DevOps Assignment - ITA730 - Dipesh Sunil Kathole.
## Project Structure

```
.
├── ansible/                    # Ansible playbooks for automation
│   ├── deploy-stack.yml       # Docker stack deployment playbook
│   ├── install-docker.yml     # Docker installation playbook
│   ├── inventory             # Ansible inventory file
│   └── swarm-init.yml        # Docker Swarm initialization playbook
│
├── ci/                        # CI/CD Configuration
│   ├── github-actions.yml    # GitHub Actions workflow
│   └── Jenkinsfile          # Jenkins pipeline configuration
│
├── django_app/               # Django Web Application
│   ├── manage.py            # Django management script
│   ├── requirements.txt     # Python dependencies
│   ├── myapp/              # Main application
│   │   ├── __init__.py
│   │   └── views.py
│   ├── myproject/          # Project configuration
│   │   ├── __init__.py
│   │   ├── settings.py
│   │   ├── urls.py
│   │   └── wsgi.py
│   └── templates/          # HTML templates
│       ├── home.html
│       ├── login.html
│       └── register.html
│
├── docker/                  # Docker Configuration
│   ├── docker-compose.yml  # Docker Compose configuration
│   ├── Dockerfile.web      # Web application Dockerfile
│   └── init.sql           # Database initialization script
│
├── scripts/                # Utility Scripts
│   └── bootstrap.sh       # Environment setup script
│
├── selenium/              # Automated Testing
│   └── test_app.py       # Selenium test scripts
│
└── terraform/            # Infrastructure as Code
    ├── main.tf          # Main Terraform configuration
    ├── terraform-key.pem # SSH key for instances
    ├── terraform.tfstate # Terraform state file
    └── variables.tf     # Variable definitions
```

## Components

1. **Django Web Application**: A web application built with Django framework
2. **Docker Configuration**: Containerization setup with Docker and Docker Compose
3. **CI/CD Pipeline**: Implemented using GitHub Actions and Jenkins
4. **Infrastructure as Code**: Using Terraform for infrastructure provisioning
5. **Configuration Management**: Ansible playbooks for automation
6. **Automated Testing**: Selenium tests for web application

## Project Architecture

```
┌─────────────────┐     ┌─────────────────┐
│   GitHub Repo   │────>│  Jenkins Server  │
└────────┬────────┘     └────────┬────────┘
         │                       │
         │                       ▼
         │               ┌─────────────────┐
         │               │  Docker Swarm   │
         │               │    Cluster      │
         │               └────────┬────────┘
         │                       │
         ▼                       ▼
┌─────────────────┐     ┌─────────────────┐
│    Terraform    │────>│     Ansible     │
└────────┬────────┘     └────────┬────────┘
         │                       │
         │                       ▼
         │             ┌───────────────────┐
         │             │  Infrastructure   │
         └────────────>│   (AWS EC2)      │
                      └───────────────────┘

┌─── Application Stack ───┐
│ ┌─────────────────┐    │
│ │  Django Web App │    │
│ └────────┬────────┘    │
│          │             │
│ ┌────────▼────────┐    │
│ │   PostgreSQL    │    │
│ └─────────────────┘    │
└─────────────────────────┘
```

### Flow Description:

1. **Development & Version Control**:
   - Code is pushed to GitHub repository
   - Triggers CI/CD pipeline in Jenkins

2. **Infrastructure Provisioning**:
   - Terraform creates AWS EC2 instances
   - Sets up networking and security groups
   - Provisions required infrastructure resources

3. **Configuration & Deployment**:
   - Ansible configures the EC2 instances
   - Installs Docker and initializes Swarm cluster
   - Sets up manager and worker nodes

4. **Application Deployment**:
   - Jenkins builds Docker images
   - Deploys application stack to Docker Swarm
   - Manages container orchestration

5. **Monitoring & Testing**:
   - Selenium runs automated tests
   - Application health is monitored
   - Logs are collected and analyzed
## Infrastructure (EC2 Instances)
- **Controller**: 44.193.223.96
- **Manager**: 34.230.229.232  
- **Worker A**: 13.218.252.195
- **Worker B**: 50.19.133.201

## Quick Start

### Bootstrap Everything:
```bash
chmod +x scripts/bootstrap.sh
./scripts/bootstrap.sh
```

### Access Points:
- **Application**: http://34.230.229.232:8000
- **Jenkins**: http://44.193.223.96:8080

## Manual Deployment

### 1. Terraform:
```bash
cd terraform
terraform init
terraform apply
```

### 2. Ansible:
```bash
cd ansible
ansible-playbook -i inventory install-docker.yml
ansible-playbook -i inventory swarm-init.yml
ansible-playbook -i inventory deploy-stack.yml
```

## CI/CD Pipeline
Jenkins automatically builds and deploys on every push to ITA730 branch.

OUTPUT:<br>
Registeration Page :- Enter roll no and Admission no 
![register page](https://github.com/dipeshskathole/ITA730_DevOpsAssign_12/raw/ITA730/outputs/registeration%20page.jpg)<br>
Login Page <br>
![Login Page](https://github.com/dipeshskathole/ITA730_DevOpsAssign_12/raw/ITA730/outputs/login%20page.jpg)<br>
Home Page :-<br>
![Home Page](https://github.com/dipeshskathole/ITA730_DevOpsAssign_12/raw/ITA730/outputs/home%20page.jpg)
