# base command list

vagrant box add <name> <url>

vagrant box list

vagrant box remove <name>

vagrant box repackage <name> 

vagrant init [box-name] [box-url]

vagrant up [vm-name] [--[no-]provision] [-h]

vagrant destroy [vm-name]

vagrant suspend [vm-name]

vagrant reload [vm-name]

vagrant resume [vm-name]

vagrant halt [vm-name]

vagrant status [vm-name] 

vagrant package [vm-name] [--base name] [--output name.box]

[--include one,two,three] [--vagrantfile file]

vagrant provision [vm-name]

vagrant ssh [vm-name] [-c command] [-- extra ssh args]

vagrant ssh-config [vm-name] [--host name]
