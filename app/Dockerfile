# Use an official Python runtime as a parent image
FROM python:latest

RUN useradd -m myuser
USER myuser

# Set the working directory in the container to /app
WORKDIR /app

# Устанавливаем правильные права доступа
RUN mkdir -p /app/venv && chown -R $USER /app


# Install virtualenv
RUN pip install virtualenv

# Create a virtual environment
RUN python -m venv venv

# Add the current directory contents into the container at /app
COPY . /app

# Install the required dependencies
RUN /app/venv/bin/pip install -r requirements.txt



# Make port 8088 available to the world outside this container
EXPOSE 8088

# Run clock.py when the container launches
# CMD ["python", "clock.py"]
ENV FLASK_APP=clock.py

# Adjust the PATH to include the virtual environment
ENV PATH="/app/venv/bin:$PATH"

# Run the Flask app
CMD ["flask", "run", "--host=0.0.0.0", "--port=8088"]
