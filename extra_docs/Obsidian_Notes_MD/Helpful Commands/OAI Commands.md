

| Build target (inside /cmake_targets)             | ./build_oai -w USRP --ninja --nrUE --gNB --build-lib "nrscope" -C                                                                                    |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| note: -C clears cache                            |                                                                                                                                                      |
| Run OAI build in /cmake_targets/ran_build/build/ | ./nr-softmodem -O ../../../targets/PROJECTS/GENERIC-NR-5GC/CONF/gnb.sa.band78.fr1.106PRB.usrpb210.conf --gNBs.[0].min_rxtxtime 6 -E --continuous-txc |
