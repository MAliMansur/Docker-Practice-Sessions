FROM ubuntu

WORKDIR /app

COPY requirements.txt /app
COPY devops /app

RUN apt-get update && \
    apt-get install -y python3 python3-venv python3-pip

# Create a virtual environment
RUN python3 -m venv /app/venv

# Activate the virtual environment and install the dependencies
RUN /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r requirements.txt

# Add the virtual environment's Python to PATH
ENV PATH="/app/venv/bin:$PATH"

# Change the working directory to devops if needed
WORKDIR /app/devops

# Set the entry point to use the virtual environment's Python
ENTRYPOINT ["python3"]
CMD ["/app/manage.py", "runserver", "0.0.0.0:8000"]




