.. _mender_method:

###########
The Method
###########

The approach was to set up a Mender server and client to test the feasibility of deploying updates.

1. **Server and Client Setup:** A mock server and client were set up on NUCs to test the basic functionality of Mender.
2. **Test Deployment:** A test update was successfully launched using the Mender server.
3. **UHD Filesystem Update:** The possibility of updating the UHD filesystem remotely was investigated. It was discovered that while the filesystem can be updated with Mender, the FPGA images require the `uhd_image_loader` tool. The proposed solution is to use Mender to update the filesystem and then execute a script to load the FPGA image (If updating the FPGA image is required... which it shouldnt be).
