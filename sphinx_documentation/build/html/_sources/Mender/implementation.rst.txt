.. _mender_implementation:

################
Implementation
################

Here is a guide to setting up a Mender server and client for this purpose.

**Server Installation:**
The server installation is a three-step process involving Kubernetes, Storage, and the Mender Server itself. A solid understanding of Kubernetes and storage solutions is recommended. The official Mender documentation provides a detailed guide: `Production Installation with Kubernetes <https://docs.mender.io/development/server-installation/production-installation-with-kubernetes/kubernetes>`_

*Key Configuration Notes:*
- A domain name is required; an IP address alone is not sufficient. You can assign a domain in `/etc/hosts` for testing purposes (e.g., `mender.example.com`).
- You must choose to use either HTTP or HTTPS for the server; you cannot use both.

**Client Installation:**
1.  Install the Mender client using the apt repository. More information can be found in the Mender documentation: `Install using the apt repository <https://docs.mender.io/development/downloads#install-using-the-apt-repository>`_
2.  Use the `mender-setup` command to configure the client. You will need a token generated from your Mender server's web interface. Ensure the server URL is formatted correctly with either http or https.

**Updating the N320:**
Ettus Research provides a guide for this process: `N320 Getting Started Guide <https://kb.ettus.com/USRP_N300/N310/N320/N321_Getting_Started_Guide>`_

The process involves two main steps:
1.  Use Mender to update the filesystem.
2.  Use a script, also deployed via Mender, to load the FPGA images using `uhd_image_loader`.

An alternative to a dedicated server is to run the Mender command with the update file on each base station server. This is less automated but still more efficient than manually updating each N320.
