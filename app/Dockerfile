# Use an official Python runtime as a parent image
FROM python:latest

# Create a non-root user and switch to that user
RUN useradd -m myuser

# Set the working directory in the container to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . /app

# Change ownership of /app to myuser
RUN chown -R myuser:myuser /app

# Switch to non-root user
USER myuser

# Install virtualenv
RUN pip install virtualenv

# Create a virtual environment
RUN python -m venv venv

# Activate the virtual environment and install dependencies
RUN /app/venv/bin/pip install -r /app/requirements.txt

# Make port 8088 available to the world outside this container
EXPOSE 8088

# Set environment variable for Flask app
ENV FLASK_APP=clock.py

# Adjust the PATH to include the virtual environment
ENV PATH="/app/venv/bin:$PATH"

# Run the Flask app
CMD ["flask", "run", "--host=0.0.0.0", "--port=8088"]
