Required postgres database

You could use standart postgres image

To start it:

docker network create books-back-net //create network

docker run -d --name database --net books-back-net -e POSTGRES_USER=django -e POSTGRES_PASSWORD=django -v ${HOME}/docker-task/postgres-data/:/var/lib/postgresql/data -p 5432:5432 postgres

Attach backend to the same networks:

docker network connect books-back-net BACKEND_CONTAINER_NAME
