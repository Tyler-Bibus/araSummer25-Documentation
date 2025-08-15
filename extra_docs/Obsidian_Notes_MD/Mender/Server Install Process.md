This can be broken up into 3 major steps:
1. Kuberetics
2. Storage (SeaweedFS for local)
3. Mender Server

This is just general notes, doesn't include any specifics

It is preferred if you have a more solid grasp on kuberetics and storage than I did.
Here is the link
https://docs.mender.io/development/server-installation/production-installation-with-kubernetes/kubernetes
Change the domain to our domain or localhost if hosting locally (as I am)
# Kubernetes
1. Install kubernetes (K3s)
2. Install Helm

# Storage
1. set seaweek yml config
2. Export keys needed for later mender steps

# Mender Server
1. We will use an Ingress for Traefik (which is included in K3s)
2. Set External MongoDB (install mongo if needed)
3. Create mender values yml for helm
4. install mender server
5. add admin user
6. 
defaut admin credentials as I did
username:`demo@mender.io`
password: `demodemo`

Config notes:
You cannot use a IP, you must use a domain. You can assign domains in */etc/hosts/*

For my server I used *mender.example.com*

It is important to note, for our uses, we either need a cert-manager for https, or we can use http for a simpler setup, albeit less secure.

**NOTE: you must use either https or http, you cannot use both!**

## Mender Client

First download mender using apt
see [this](https://docs.mender.io/development/downloads#install-using-the-apt-repository) document for more info on how to do that


The Mender client is very straightforward, just make sure to use the token generated in the server at 
domain.com/ui/settings/my-profile
and generate a new token.

Also set an appropriate device-type

Then use mender-setup to set up the client. It is crucial that the url is formatted correctly, as if it is https or http when it should be one or the other it could very well break it.

More info on the install guide can be found [here.](https://docs.mender.io/development/client-installation/install-with-debian-package)