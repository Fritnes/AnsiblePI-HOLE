Role "Pi-hole"
=========

https://pi-hole.net/

Role Variables
--------------

docker_folder: "/opt"
pihole_docker_version: "3"
pihole_container_name: "pihole"
pihole_container_image: "pihole/pihole:latest"
pihole_ports:
   - { external_port: "8100", internal_port: "80/tcp"}
   - { external_port: "53", internal_port: "53/udp"}
   - { external_port: "53", internal_port: "53/tcp"}

pihole_volumes:
   - { external_valume: "./etc-pihole/", internal_valume: "/etc/pihole/"}

pihole_env:
   - { env_name: "TZ", env_volume: "Europe/Kiev"}
   - { env_name: "WEBPASSWORD", env_volume: "test"}
   - { env_name: "PIHOLE_DNS_", env_volume: "8.8.8.8;1.1.1.1"}
   - { env_name: "DHCP_ACTIVE", env_volume: "false"}
   - { env_name: "PIHOLE_DOMAIN", env_volume: "lan"}

Example Playbook
----------------

    - hosts: servers
      roles:
        - { role: AnsiblePI-HOLE, when: ansible_system == 'Linux' }

Author Information
------------------

fritnes
https://github.com/Fritnes
