<h2> What are Vagrant Boxes ?</h2>

  - Boxes are the package format for Vagrant environments.
  - They can be used on any platform that Vagrant supports.
  - Download Vagrant Boxes: https://app.vagrantup.com/boxes/search
  - vagrant box commands:
    
    + ```vagrant box add <ADDRESS>```
    + ```vagrant box list```
    + ```vagrant box outdated```
    + ```vagrant box prune```
    + ```vagrant box remove <NAME>```
    + ```vagrant box repackage <NAME> <PROVIDER> <VERSION>```
    + ```vagrant box update```
    + ```vagrant init hashicorp/precise64```

<h2>Box Versioning</h2>

  - Since Vagrant 1.5, boxes support versioning.
  - You can update boxes with ```vagrant box update```:
    + This will download and install the new box.
    + This will not magically update running Vagrant environments.
  - You can constrain a Vagrant environment to a specific version.
  - Constraints can be any combination of the following: = X, > X, < X, >= X, <= X, ~> X:
    + ```config.vm.box_version = X```
  - You can also configure Vagrant to automatically check for updates:
    + ```config.vm.box_check_update = false```
  - Vagrant does not automatically prune old versions:
    + ```vagrant box prune```
