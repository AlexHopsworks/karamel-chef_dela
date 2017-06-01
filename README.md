# karamel-chef
This chef cookbook installs Karamel. Used by Vagrant to provision multi-node clusters.

1. Run the init script to download chef-dk and karamel to the downloads directory.

1a. Create your own cluster by copying an existing Karamel cluster definition. If your name is John, call it 'hopsworks.1.john'. Then customize it. 

2. To start a Hopsworks VM, use the run.sh script. The parameters are: <operating sys>(ubuntu or centos), number of VMs in the vagrant configuration (1 or 3),  <cluster-postfix-name> (john, hopsworks, jim, virtualbox, etc), [no-random-ports]  - this will forward the ports in the Vagrantfile.

For example,
./run.sh ubuntu 1 jim no-random-ports

3. To shutdown your cluster, run the kill.sh script:

./kill.sh 

# installation details
If you want to run multiple instances of VMs using karamel-chef, even if you checkout karamel-chef in a different folder, it overrides the machines definitions in ~/VirtualBox VMs, essentially destroying your other VMs. In order to change the default directory of VirtualBox do
```bash
VBoxManage setproperty machinefolder $HOME/VBox_alternative_dir
```
# tunnel access
```bash
ssh -L ${LOCAL_PORT}:${REMOTE_MACHINE}:${REMOTE_PORT} ${REMOTE_USER}@${REMOTE_MACHINE}
```

# tunnel access bridge machine
```bash
ssh -L localhost:${LOCAL_PORT}:${REMOTE_MACHINE}:${REMOTE_PORT} ${REMOTE_BRIDGE_USER}@${REMOTE_BRIDGE_MACHINE}
```
