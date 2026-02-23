FROM jenkins/jenkins:lts

USER root

# Install Docker from Debian repository
RUN apt-get update && \
    apt-get install -y docker.io && \
    apt-get clean

# Add Jenkins to docker group
RUN usermod -aG docker jenkins

USER jenkins