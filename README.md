# docker-symfony-nginx-pgsql

### Installation

You can check the `.env` file to rename compose project

1. First run `docker-compose up`

2. Get the container id using `docker ps` <br> and get the id of the container named _COMPOSE_PROJECT_NAME_ _php (only the first few char are needed)

3. Then you connect to the php container using and `docker exec -it <container_id> bash`
 and do `symfony new . --webapp`
4. Go to http://localhost :)

### Informations

Composer and symfony CLI are installed on the PHP container


### TODO
* Add php extensions as .env var
* Add php version as .env var