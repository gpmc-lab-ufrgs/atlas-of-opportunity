# Atlas of Opportunity Server Administration

## Hosting Environment

The Atlas is structured like a typical modern web application with a frontend client, a backend server, and a supporting database. A development environment might use one machine to run all services, but production environments should use a separate machine for each service.

The Atlas is dockerized software, meaning its services can be built and deployed in nearly any environment while remaining isolated from other services in that environment. Any system capable of running Docker should be able to run the Atlas of Opportunity. It is possible, but not recommended, to run each service directly on a host machine without Docker, as using Docker reduces the chances for bugs caused by differences between server environments.

## Development Environment

The Atlas is configured to run in a development environment by default. To start a server with a default dataset, simply checkout the code from its repo on GitHub and build and run the project's default Docker Compose configuration:

```
git clone https://github.com/gpmc-lab-ufrgs/atlas-of-opportunity.git
cd atlas-of-opportunity
git submodule update --init --recursive 
```

```
cd atlas-backend
docker compose up -d
```

```
cd atlas-frontend
yarn
yarn start
```

To full instructions see the README file in [atlas-backend](https://github.com/gpmc-lab-ufrgs/atlas-backend/tree/189baf86ac397cda9270fd62e391ae8d928c7334) and atlas-[front-end](https://github.com/gpmc-lab-ufrgs/atlas/tree/007c87577fc5197bcea74f307d29e96db2ddb123) repository.

Building the Docker images only needs to happen once but will likely take several minutes to complete. Running the project for the first time includes database imports, precomputation of some models, and compilation of the frontend for development mode which will also likely take several minutes.

When all of the containers have finished starting up, a development version of the frontend should be reachable at http://localhost:3000/, the backend at http://localhost:8000/, and the database at http://localhost:5432/.

## Production Environment

The recommended setup for production environments is a high-availability, managed database and redundant machines for the frontend and backend, all proxied behind a load balancer. MIT Connection Science uses AWS for its own production deployment of the Atlas, but that is not an endorsement of AWS over other hosting solutions.

## Uploading Spreadsheets

To load dictionary and data spreadsheets into the database, go to http://...:3000/loaddata and fill in the form. Authentication is required. Each worksheet must have a data tab named 'atlas'. When the upload is complete, you will receive an email with the status of the upload and an on-screen message.

