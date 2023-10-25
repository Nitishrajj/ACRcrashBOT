# Use a base image of Ubuntu 16.04
FROM ubuntu:16.04
# Set the timezone to Asia/Kolkata
RUN ln -fs /usr/share/zoneinfo/Asia/Kolkata /etc/localtime

# Install Python 3.5 and other dependencies
RUN apt-get update && \
    apt-get install -y python3.5 \
    python3.5-dev \
    python3-setuptools \
    curl

# Install PIP3
RUN curl --silent --show-error --retry 5 https://bootstrap.pypa.io/pip/3.5/get-pip.py | python3.5

# Create a directory for your application
RUN mkdir /core

# Copy requirements.txt and install Python packages
ADD requirements.txt /crashreporter/requirements.txt
RUN pip3 install -r /crashreporter/requirements.txt

# Copy the entire crashreporter directory
ADD ./crashreporter /crashreporter

# Set the working directory
WORKDIR /crashreporter/src

# Define the entry point to run main.py every 6 hour interval
# CMD while true; do /usr/bin/python3 main.py; sleep 21600; done

