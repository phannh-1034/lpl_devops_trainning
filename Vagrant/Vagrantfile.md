1. What is this ?
  - Describe the type of machine required for a project, and how to   configure and provision these machines.
  - The syntax of Vagrantfile is Ruby.
2. Lookup Path
  - Vagrant climbs up the directory tree looking for the first Vagrantfile it can find, starting first in the current directory.
  - Example: run ```vagrant``` in ```/home/lucifer/projects/foo```
  ```
    /home/lucifer/projects/foo/Vagrantfile
    /home/lucifer/projects/Vagrantfile
    /home/lucifer/Vagrantfile
    /home/Vagrantfile
    /Vagrantfile
  ```
  - Can change the starting dir where Vagrant looks for a Vagrantfile by setting the ```VAGRANT_CWD``` env to some other path.
3. Configuration Version
  ```
    Vagrant.configure("#{vagrant_version}") do |config|
    # ...
    end
  ```
4. Tip & Trick
  * Loop Over VM Definitions
    ```
      (1..3).each do |i|
        config.vm.define "node-#{i}" do |node|
          node.vm.provision "shell",
            inline: "echo hello from node #{i}"
        end
      end
    ```
  * Overwrite host locale in SSH session
    ```
      ENV["LC_ALL"] = "en_US.UTF-8"

      Vagrant.configure("2") do |config|
        # ...
      end
    ```
    NOTE: The change is only visible within the ```Vagrantfile```.
5. Config details:
  * config.vm:
    - ```allow_fstab_modification``` (boolean): Default Value is True. Identify fstab entries for synced folders.
    - ```allow_hosts_modification``` (boolean): Default is True. Identify Vagrant can writing to /etc/hosts.
    - ```allowed_synced_folder_types``` (array of strings): The elements of the array should be the name of the synced folder plugin.
    - ```base_mac``` (string): Define MAC address to be assigned to the default NAT interface on the guest. Support for this option is provider dependent.
     - ```base_address``` (string): Define the IP address to be assigned to the default NAT interface on the guest. Support for this option is provider dependent.
    - ```boot_timeout``` (integer): Default: 300 seconds. The time that Vagrant will wait for the machine to boot and be accessible.
    - ```box``` (string): This configures what box the machine will be brought up against. Should be the name of an installed box or shorthand name of a box in [HashiCorp's Vagrant Cloud](https://developer.hashicorp.com/vagrant/vagrant-cloud).
    - ```box_check_update``` (boolean): Default is True. Check for updates to the configured box on every run ```vagrant up```.

        ...

    - ```provisions```: Configures [provisioners](https://developer.hashicorp.com/vagrant/docs/provisioning) on the machine.
    - ```synced_folder```: configures [synced_folder](https://developer.hashicorp.com/vagrant/docs/synced-folders) on a machine, so that folders on your host machine can be synced to and from the guest machine.
    - ```usable_port_range``` (range): Range of ports Vagrant can use for handling port collisions and such. Default to ```2200..2250```.
  * config.ssh:
    - ```compression``` (boolean): Default is true.
    - ```connect_timeout``` (integer): Number of seconds to wait for establishing an ssh connection to the guest. Default is 15.
    - ```config``` (string): Path to a custom ssh_config file to use for configuring the ssh connections.
    - ```das_authentication``` (boolean): Default is True.
    - ```export_command_template``` (string): Define template used to generate exported env in the active session.
    - ```extra_args``` (array of strings): list args pass to ssh executable.
    - ```forward_agent``` (boolean): Default is false. Agent forwarding over ssh connections is enable or disable.
    - ```forward_env``` (arr of strings): arr of host env to forward to the guest.
    - ```shell``` (string): shell to use when exe ssh command from Vagrant. By default this is ```bash -l```.

        ....
  * config.winrm:
  * config.winssh:
  * config.vagrant: