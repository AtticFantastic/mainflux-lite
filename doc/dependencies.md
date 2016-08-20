# Dependencies
Mainflux Lite server is connected to `MongoDB` and `InfluxDB` on southbound interface.

This is why to run Mainflux Lite server you have to have running:
- [MongoDB](https://github.com/mongodb/mongo)
- [InfluxDB](https://github.com/influxdata/influxdb)

Installation and start of these services depends the operating system running on host (e.g. for Debian you can use `apt-get` to fetch and install these), so you must follow the installation instructions for each of the project.

However, each of these projects provides an official Docker image which can be pulled from DockerHub and started in a separate container (each in separate terminal if not detached):
```bash
docker run -p 27017:27017 -it mongo
docker run -p 8086:8086 -it influxdb
```
Now you can run `mainflux-lite`:
```bash
./mainflux-lite ./config/config.yml
```

> N.B. Since `mongo` and `influxdb` containers are not started in the composition (via `docker-compose`), but manually, we have to bind port of each container to development host. This way `mainflux-lite` binary that is started on the host will see correct services it expects on `localhost`

For more info about Docker images you can look [here](https://github.com/Mainflux/mainflux-lite/blob/master/doc/docker.md).