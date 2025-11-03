# ⚙️ Ansible Nginx Load Balancer Automation

This project automates the setup and configuration of an **Nginx Load Balancer** using **Ansible** — a real-world DevOps use case that improves scalability, reliability, and automation across distributed systems.

---

## 🚀 Features
- ✅ Installs and configures Nginx automatically
- 🧩 Uses Jinja2 templating for dynamic backend configuration
- 🖥️ Supports both Debian and RHEL systems
- ♻️ Automatically restarts Nginx when configuration changes
- 📦 Fully reusable and scalable for production-grade setups

---

## 🗂️ Repository Structure
ansible-nginx-loadbalancer/
│
├── nginx_loadbalancer.yml # Main Ansible playbook
├── templates/
│ └── nginx_lb.conf.j2 # Nginx configuration template
├── inventory.ini # Inventory file with host details
└── README.md # Documentation

yaml
Copy code

---

## ⚡ Prerequisites
- Ansible installed on your control node  
- SSH access to target servers  
- Sudo privileges on the load balancer server  

---

## 🧠 Example Inventory File
ini
[loadbalancer]
192.168.1.100 ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/id_rsa
▶️ Run the Playbook
bash
Copy code
ansible-playbook -i inventory.ini nginx_loadbalancer.yml
💡 How It Works
Detects the OS type (Debian/RHEL)

Installs Nginx accordingly

Generates a dynamic configuration file via Jinja2

Restarts Nginx if configuration changes

Keeps your system consistent and idempotent

🔧 Example Configuration Output
The playbook creates a load balancer config like:

nginx
Copy code
upstream backend {
    server 192.168.1.101:80;
    server 192.168.1.102:80;
}

server {
    listen 80;
    location / {
        proxy_pass http://backend;
    }
}
🧑‍💻 Author
Prashanth Teja
