FROM ubuntu

# Set the working directory
WORKDIR /app

# Copy the requirements file and the devops directory into the container
COPY requirements.txt /app
COPY devops /app/devops

# Update package list and install Python and pip
RUN apt-get update && \
    apt-get install -y python3 python3-venv

# Create and activate a virtual environment
RUN python3 -m venv venv
ENV PATH="/app/venv/bin:$PATH"

# Install the required Python packages
RUN pip install --upgrade pip && \
    pip install -r requirements.txt

# Set the working directory to the devops directory
WORKDIR /app/devops

# Set the entry point and default command
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
