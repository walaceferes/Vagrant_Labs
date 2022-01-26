# Simple tamplate of vagrantfile with Virtualbox: Set setup machine, network NAT MODE. Provisioning only one machine
machines = {
  "wofereslocal" => {"memory" => "1024", "cpu" => "2", "ip" => "20", "image" => "[imagename]"}
}

Vagrant.configure("2") do |config|
  machines.each do |name, conf|
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
      end
    end
  end
end
