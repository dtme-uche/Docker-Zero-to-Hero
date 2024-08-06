# Use the official Ubuntu image from Docker Hub
FROM ubuntu:latest

# Set the working directory in the container
WORKDIR /app

# Copy the requirements.txt file into the container
COPY requirements.txt .

# Update the package list and install Python, pip, and venv
RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

# Create and activate a virtual environment, then install the required Python packages
RUN python3 -m venv venv && \
    . venv/bin/activate && \
    pip install --upgrade pip && \
    pip install -r requirements.txt

# Copy the rest of your application code into the container
COPY devops /app

# Set the entry point and command to run your application
ENTRYPOINT ["./venv/bin/python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]

