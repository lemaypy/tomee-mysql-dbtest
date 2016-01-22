# tomee-mysql-dbtest
test connection between tomee and mysql with a simple jsp application
# Run

## Fig
* `docker-compose up -d`

Then run `docker-compose ps` to find the app port.

## Standalone

* `docker run -d -P -e MYSQL_USER=java -e MYSQL_PASSWORD=java -e MYSQL_DATABASE=javatest --name mysql orchardup/mysql`
* `docker run -ti --rm --link mysql:mysql -v $(pwd):/host --entrypoint /bin/bash orchardup/mysql -c "sleep 4; mysql -u java --password=java -h mysql javatest < /host/init.sql; exit 0"`
* `docker build -t javatest .`
* `docker run -ti -P --rm --link mysql:mysql javatest`

You should be able to access the app on http://\<docker-host-ip\>:\<app-port\>/dbtest
