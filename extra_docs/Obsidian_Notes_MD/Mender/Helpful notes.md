If Helm says the kubernetics cluster is unreachable, try running
````yaml
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
````
or this inline with the helm command
`--kubeconfig /etc/rancher/k3s/k3s.yaml`

In order to access the GUI you need to add the domain to /etc/hosts
for now we are using mender.example.com, so add the ip of the server and mender.example.com like so
`10.26.49.44 mender.example.com`


ARA Mender Login
ara@iastate.edu
AraSecurePhrase