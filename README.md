E-Commerce Application Ansible Configuration
This project demonstrates the use of Ansible to automate the deployment of an e-commerce application with separate Docker containers for the frontend, backend, and MongoDB database.

Project Structure
.
├── Vagrantfile
├── playbook.yml
├── vars/
│   └── main.yml
└── roles/
    ├
    ├── docker/
    │   └── tasks/
    │       ├── main.yml
    │── clone/
    │   └── tasks/
    │       └── main.yml
    ├── mongodb/
    │   └── tasks/
    │       └── main.yml
    ├── backend/
    │   └── tasks/
    │       └── main.yml
    └── frontend/
        └── tasks/
            └── main.yml
Prerequisites
Vagrant
VirtualBox
Ansible
Getting Started
Clone this repository
Navigate to the project directory
Run the following commands:
bash
# Start and provision the Vagrant VM
vagrant up

# If you need to re-run the Ansible playbook
vagrant provision
Application Access
Once the playbook has run successfully, you can access the application at:

Frontend: http://localhost:3000
Backend API: http://localhost:5000
Features Implemented
Ansible Playbook Structure
Variables stored in dedicated files
Role-based task organization
Blocks and tags for better organization
Idempotent tasks
Docker Container Setup
MongoDB container
Backend Node.js container
Frontend React container
Docker network for inter-container communication
Automated Workflow
Repository cloning
Docker and Docker Compose installation
Container building and deployment
Network configuration
Testing the Application
Navigate to http://localhost:3000 in your browser
Use the "Add Product" functionality to test if the application is working correctly
View the products in the store section
Troubleshooting
If you encounter any issues, you can:

Check the Ansible logs: vagrant provision --debug
SSH into the VM: vagrant ssh
Check Docker container status: docker ps -a
View container logs: docker logs <container_name>
