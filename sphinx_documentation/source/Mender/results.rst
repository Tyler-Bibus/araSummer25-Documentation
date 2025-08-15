.. _mender_results:

#########
Results
#########

The investigation demonstrated that it is possible to remotely update the USRP N320 SDRs.

- **Mock Environment:** Successfully set up a mock Mender server and client.
- **Test Update:** Launched a successful test update.
- **UHD Filesystem:** Determined a method for updating the UHD filesystem remotely.

An issue was encountered when uploading the UHD filesystem artifact to the mock server, likely due to the artifact's large size and the server's limited resources. A more powerful server or a load balancer would likely resolve this.
