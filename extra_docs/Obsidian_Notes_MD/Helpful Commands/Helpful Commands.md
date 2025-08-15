
| What                                              | Command                                                                                                             |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Start a srsRAN gNB with a config                  | ./gnb -c config.yml                                                                                                 |
| View the bottom of a live log                     | tail -f /name.log                                                                                                   |
| Start Docker Image                                | ```sudo docker run -itd --name srsRAN_23_10 --privileged --network host arawirelesshub/srsran:release_23_10 bash``` |
| Build docker image                                | docker build -t <image_name> .<br>                                                                                  |
| Build srsRAN with gcc version compatibility error | cmake../  && cmake -DCMAKE_CXX_FLAGS="-Wno-error=array-bounds" ../ \                                                |
| get into docker container                         | sudo docker exec -it <container_name> bash                                                                          |
| View ubuntu version                               | lsb_release -a                                                                                                      |
| CMake with gcc and g++ and c++ version 9          | cmake ../ -DCMAKE_C_COMPILER=/usr/bin/gcc-9 -DCMAKE_CXX_COMPILER=/usr/bin/g++-9                                     |
| Commit docker container                           | sudo docker commit <container_name> <group_>/<repository*>:<version*>                                               |
| Push docker container                             | sudo docker push <container_name> <group*>/<repository*>:<version*>                                                 |
