Vagrant.configure("2") do |config|
# Defining a New VM named server and assign to a variable named dev
  config.vm.define "virtualbox" do |dev| 
    dev.vm.hostname = "devbox"
    dev.vm.box = "ubuntu/focal64" 
    dev.vm.memory = "2048" 
  end

  config.vm.provision "ansible" do |ansible| 
    ansible.verbose = "v" 
    ansible.playbook="playbook.yaml" 
    end 
end
