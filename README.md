# Anudesh

<p align="center">
    <em>An open source platform to annotate and label data at scale</em>
</p>


<p align="center">
    <a href="https://opensource.org/licenses/MIT" target="_blank">
        <img src="https://img.shields.io/badge/License-MIT-green.svg" alt="License: MIT">
    </a>
</p>

***

*[Anudesh](http://Anudesh.ai4bharat.org/)* is an open source platform to annotate Lare language models' data at scale, built with a vision to enhance digital presence of under-represented languages in India.

## Cloning this Master Repo
    git clone --recurse-submodules https://github.com/AI4Bharat/Shoonya

## Backend Setup

### Clone the Anudesh-Backend repository from GitHub to your local machine.
    git clone https://github.com/AI4Bharat/Anudesh-Backend.git
            
### Create a virtual environment for the project. Replace  with your preferred environment name.
    python3 -m venv 

### Activate the virtual environment. This ensures that the packages you install are isolated from the global Python environment.
    source /bin/activate

### Install all required Python packages listed in the requirements-dev.txt file.
    pip install -r deploy/requirements-dev.txt

### Set up the environment variables needed for the project by copying the example environment file.
    cp .env.example ./backend/.env

### Generate a new secret key for Django (within the virtual environment):
### Open a Python shell.
    python backend/manage.py shell

    # Import the utility function to generate a secret key.
    >> from django.core.management.utils import get_random_secret_key

    # Generate and print a new secret key.
    >> get_random_secret_key()

#### Copy the generated secret key and paste it into the .env file as the value for SECRET_KEY.

### Docker Installation
### Build the Docker containers as defined in the docker-compose-local.yml file.
    docker-compose -f docker-compose-local.yml build

### Run the containers in detached mode (-d flag). This will start up all the services defined in the Docker Compose file.
    docker-compose -f docker-compose-local.yml up -d

### Run Migrations
#### The following steps are required only when you run the project for the first time or after making changes to the models.

    # Check if there are any pending migrations.
    docker-compose exec web python backend/manage.py makemigrations 

    # Apply all pending migrations to the database.
    docker-compose exec web python backend/manage.py migrate

### Create a superuser for accessing the Django admin interface (required only once).
    docker-compose exec web python backend/manage.py createsuperuser

### Run the Django development server within the Docker container.
    docker-compose exec web python backend/manage.py runserver

## Frontend Setup

### Clone the Anudesh-Frontend repository from GitHub to your local machine.
    git clone https://github.com/AI4Bharat/Anudesh-Frontend.git

### Change directory to the newly cloned Anudesh-Frontend folder.
    cd Anudesh-Frontend

### Install the necessary dependencies for the project. 
#### The --force flag is used to bypass conflicts with the existing dependencies.
    npm i --force

### Start the development server. This will run the frontend application on a local server.
    npm run dev
