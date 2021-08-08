# record
```
mongo -u admin -p 'abc123' --authenticationDatabase 'admin'

mongo --port 27017 -u admin -p '123456' --authenticationDatabase 'admin'

db.createUser({ user: "admin", pwd: "123456", roles: [{ role: "userAdminAnyDatabase", db: "admin" }] })


db.createRole({user: "admin", pwd: "123456", role: "manageOpRole", privileges: [{ resource: { cluster: true }, actions: [ "killop", "inprog" ] }, { resource: { db: "", collection: "" }, actions: [ "killCursors" ]} ] ,roles: [] })


 db.createUser(
  {
    user: "mongo-admin",
    pwd: "123456",
    roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
  }
)

db.createUser(
  {
    user: "mongo-root",
    pwd: "123456",
    roles: [ { role: "root", db: "admin" } ]
  }
)

 db.createUser(
  {
    user: "my-user",
    pwd: "123456",
    roles: [ { role: "readWrite", db: "my-database" } ]
  }
)

use my-database

db.createUser(
  {
    user: "my-user",
    pwd: "123456",
    roles: [ { role: "readWrite", db: "my-database" } ]
  }
)

db.createUser(
  {
    user: "my-user",
    pwd: "123456",
    roles: [ 
             { role: "readWrite", db: "my-database" },
             { role: "read", db:"another-database" }
           ]
  }
)
```

```
docker run --volume=/:/rootfs:ro --volume=/var/run:/var/run:rw --volume=/sys:/sys:ro --volume=/var/lib/docker/:/var/lib/docker:ro --publish=8080:8080 --detach=true --linkinfluxsrv:influxsrv --name=cadvisor google/cadvisor -storage_driver=influxdb -storage_driver_db=cadvisor -storage_driver_host=influxsrv:8086

docker run \
  --volume=/:/rootfs:ro \
  --volume=/var/run:/var/run:rw \
  --volume=/sys:/sys:ro \
  --volume=/var/lib/docker/:/var/lib/docker:ro \
  -p 8080:8080 \
  --detach=true --link influxsrv:influxsrv \
  --name=cadvisor \
  google/cadvisor:latest \
  -storage_driver=influxdb \
  -storage_driver_db=cadvisor \
  -storage_driver_host=influxsrv:8086

  docker run -d \
  -p 3001:3000 \
  -e INFLUXDB_HOST=localhost \
  -e INFLUXDB_PORT=8086 \
  -e INFLUXDB_NAME=cadvisor \
  -e INFLUXDB_USER=root -e INFLUXDB_PASS=root \
  --link influxsrv:influxsrv \
  --name grafana \
grafana/grafana
```

```
Enable Firewalld
To enable firewalld, run the following command as root:

systemctl enable firewalld

Start Firewalld
To start firewalld, run the following command as root:

systemctl start firewalld

Check the Status of Firewalld
To check the status of firewalld, run the following command as root:

systemctl status firewalld
```

```
docker run \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=123456 \
    -v /home/data/mysql/data:/var/lib/mysql:rw \
    -v /home/data/mysql/log:/var/log/mysql:rw \
    -v /home/data/mysql/config/my.cnf:/etc/mysql/my.cnf:rw \
    -v /etc/localtime:/etc/localtime:ro \
    --name mysql8 \
    --restart=always \
    -d mysql
```
