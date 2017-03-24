# vagrant-generic-docker-machine
Connect to vagrant VMs using docker-machine generic driver

Useful commands to automate docker-machine creation

# Get the IP using the VM as $1 (argument 1) 
`function vagrantip(){
  vagrant ssh $1 -c "hostname -I | cut -d' ' -f2"
}`

# Execute the DM create using VM and IP as (arguments 1 and 2)
`function rundmc(){
  sshkey=$(vagrant ssh-config $1 | grep IdentityFile | awk '{print $2}' 2> /dev/null)
  docker-machine create -d generic --generic-ip-address $2 --generic-ssh-key $sshkey --generic-ssh-user vagrant $1
}`
