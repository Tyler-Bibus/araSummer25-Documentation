File System Upgrade - note: all data on N320 is lost when it is updated.

**Question**: Are we only worried about updating the Filesystem? or also updating the FPGA? I feel we dont need to update FPGA if they are already mounted and set to 10G?

``sudo uhd_images_downloader -t mender -t n3xx --yes``

Downloaded zip archive is in Images destination

using scp, copy the filesystem to computer that has access to Mender GUI

Add Mender image to artifacts.

Create deployment for proper SDR network.
