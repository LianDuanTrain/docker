# Install Docker on Oracle Linux 8
## Install Docker
    systemctl stop firewalld
    systemctl disable firewalld
    dnf install -y dnf-utils zip unzip
    dnf config-manager --add-repo=https://download.docker.com/linux/centos/docker-ce.repo
    dnf install -y docker-ce --nobest
    systemctl enable docker.service
    systemctl start docker.service
    systemctl status docker.service
    docker info
    docker version
    
## Manage Docker as a non-root user
    sudo groupadd docker
    sudo usermod -aG docker lian
    If testing on a virtual machine, it may be necessary to restart the virtual machine for changes to take effect.
    # useradd docker_user
     echo "lian  ALL=(ALL)  NOPASSWD: /usr/bin/docker" >> /etc/sudoers
     echo "alias docker=\"sudo /usr/bin/docker\"" >> /home/lian/.bash_profile
     su - lian
     docker ps   
     docker run hello-world

## Install Docker Compose
    curl -L "https://github.com/docker/compose/releases/download/1.27.4/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose


 
