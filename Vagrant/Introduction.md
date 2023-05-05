1. What is Vagrant?
  - Tools for building and managing virtual machine environments.
  - Provisioned on top of a provider: VirtualBox, VMWare, AWS, and Docker and another providers.
  - Provisioning tools such as shell scripts, Chef, or Puppet, Salt.
  - Out of the box providers:
    - VirtualBox
    - Hyper-V
    - Docker
  - Custom Provider are supported
  - Download Vagrant here: https://www.vagrantup.com/downloads.html
2. Vagrant Commands
  * Init:

    ```vagrant init```: initializes the current directory to be a Vagrant environment by creating a Vagrantfile

    ```vagrant up```: Create and configures guest machines according to your Vagrantfile

    ```vagrant destroy```: Stops the running and destroy all resources that were created

    ```vagrant validate```: Validates your Vagrantfile

    ```vagrant provision```: Runs any configured provisioners

    ```vagrant reload```: Runs a halt followed by an up

    ```vagrant status```: This will tell you the state of the machines

    ```vagrant ssh```: SSH into a running Vagrant machine