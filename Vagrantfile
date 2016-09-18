Vagrant.configure("2") do |config|
    config.vm.box = "gce"

    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "site.yml"
        ansible.groups = {
            "fdt"=>["default"]
        }
    end

    config.vm.provider :google do |google, override|
        google.google_project_id = ENV["GOOGLE_PROJECT_ID"]
        google.google_client_email = ENV["GOOGLE_CLIENT_EMAIL"]
        google.google_json_key_location = ENV["GOOGLE_JSON_KEY_LOCATION"]

        google.name = "fdt-dev-1"

        google.zone = "us-west1-a"

        google.machine_type = "g1-small"
        google.network = "udptransfer"
        google.image = "ubuntu-1404-trusty-v20160809a"

        override.ssh.username = ENV["SSH_USER"]
        override.ssh.private_key_path = ENV["SSH_PATH"]

    end
end
