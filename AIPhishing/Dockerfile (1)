# Use an official Ubuntu base image
FROM ubuntu:latest

# Set the maintainer label
LABEL maintainer="Aaron"

# Run updates and install necessary system packages
RUN apt-get update && apt-get install -y \
    iptables \
    iputils-ping \
    curl \
    python3 \
    python3-pip \
    python3-venv \
    build-essential \
    libffi-dev \
    libssl-dev

# Create and activate a virtual environment
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Update pip in the virtual environment
RUN pip install --upgrade pip

# Install Python packages in the virtual environment
RUN pip install numpy pandas scikit-learn scipy joblib

# Set the working directory (as root)
WORKDIR /root

# Copy the phishing_detection script into the container
COPY phishing_detection.py /root/phishing_detection.py

# Change the command to open a Bash shell
CMD ["/bin/bash"]
