# ArduPilot to Unity SIM

This sim is built using ArduPilot as a foundation. The main concept of this sim is for ArduPilots telemetry to get sent to Unity VIA ROS2 and for Unity to display the drones position.

- Original Ardupilot [GitHub](https://github.com/ardupilot/ardupilot), [website](https://ardupilot.org/)
- ROS [website](https://www.ros.org/)
- Unity [website](https://unity.com/)
- Docker [website](https://www.docker.com/products/docker-desktop/)
  
# How to get the SIM running

This simulation requires the use of WSL and Docker conatainers, ensure both are downloaded before moving forward with downloading and running the sim.

Log into WSL and clone the repository in a desired Linux directory.

First build the docker image needed for the project
```
docker build -t ardupilot .
docker build -f Dockerfile.ros -t ros-image .
```
start a network for the contianers
```
docker network create vtol-net
```

```
docker run -dit --name ros -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix:rw --network vtol-net -p 10000:10000 -p 9090:9090 ros-image bash
```

