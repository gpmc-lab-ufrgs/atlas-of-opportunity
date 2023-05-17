# Atlas of Opportunity Server Administration

## Hosting Environment

The Atlas is structured like a typical modern web application with a frontend client, a backend server, and a supporting database. A development environment might use one machine to run all services, but production environments should use a separate machine for each service.

The Atlas is dockerized software, meaning its services can be built and deployed in nearly any environment while remaining isolated from other services in that environment. Any system capable of running Docker should be able to run the Atlas of Opportunity. It is possible, but not recommended, to run each service directly on a host machine without Docker, as using Docker reduces the chances for bugs caused by differences between server environments.

## Development Environment

The Atlas is configured to run in a development environment by default. To start a server with a default dataset, simply checkout the code from its repo on GitHub and build and run the project's default Docker Compose configuration:

git clone https://github.com/gpmc-lab-ufrgs/atlas-backend.git
cd atlas-backend
docker compose up -d

