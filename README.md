# Ansible demo

## Pre-requisites
- modify sudoers file with NOPASSWD

## Usage
- update values in inventories
- setup target: `ansible-playbook required-software.playbook.yaml`

Start and confirm:
- run `podman stats` on the target host
- `ansible-playbook pythonhttp-start.playbook.yaml`
- observe container is running on target (in podman stats)
- use a browser to confirm target is serving http on port 8080

Stop:
- `ansible-playbook pythonhttp-destroy.playbook.yaml`
- observe the container is no longer running on target (in podman stats)


## Notes
- the podman version in the Ubuntu 22.04 default repo is 3.4.4. This is fine for this demo, but I'd look at getting version 5 installed before using it for real
- [community.docker.docker_compose](https://docs.ansible.com/ansible/latest/collections/community/docker/docker_compose_module.html#ansible-collections-community-docker-docker-compose-module) is deprecated and there are no ansible module for podman-compose. I would investigate using shell command to use podman-compose command in a playbook, or into writing a podman-compose module as I find keeping the container running parameters (volumes, networking, resource limitations etc...) in a compose file rather than the ansible playbook as it makes it easier test locally without ansible.
