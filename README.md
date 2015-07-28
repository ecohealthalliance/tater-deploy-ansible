# Ansible deployment for Tater.

## Deploying to an AWS instance:

Edit the inventory.ini file to add instance ip addresses you want to deploy to.  
Then run a command like this:  
`ansible-playbook site.yml -i inventory.ini --private-key ~/.keys/infrastructure.pem`

## To test deployment locally:  
`vagrant up` automatically provisions a new vm  
`vagrant ssh` drops you into a shell on the local vm  
`sudo ansible-playbook /vagrant/site.yml` to kick off a local deployment
