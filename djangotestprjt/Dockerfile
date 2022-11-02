# For more information, please refer to https://aka.ms/vscode-docker-python
FROM python:3.10.8-slim



# Keeps Python from generating .pyc files in the container
ENV PYTHONDONTWRITEBYTECODE 1

# Turns off buffering for easier container logging
ENV PYTHONUNBUFFERED 1
RUN mkdir /djangotestapp

WORKDIR /djangotestapp
# Install pip requirements
RUN pip freeze > requirements.txt
RUN pip install --upgrade pip
COPY requirements.txt /djangotestapp/
RUN pip install -r requirements.txt



COPY . /djangotestapp/
EXPOSE 8000
# Creates a non-root user with an explicit UID and adds permission to access the /app folder
# For more info, please refer to https://aka.ms/vscode-docker-python-configure-containers
#RUN adduser -u 5678 --disabled-password --gecos "" appuser && chown -R appuser /app
#USER appuser

# During debugging, this entry point will be overridden. For more information, please refer to https://aka.ms/vscode-docker-python-debug
# File wsgi.py was not found. Please enter the Python path to wsgi file.
CMD ["python3", "manage.py", "runserver", "0.0.0.0:8000",]
