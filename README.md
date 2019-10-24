Role Name
=========

This role will install docker and optionally docker-compose on a linux system.

Requirements
------------

This role needs to be used with `become: true`


Role Variables
--------------
| Variable                      | Type   | Description                        | Default
| ---                           | ---    | ---                                | ---
| docker_additional_packages    | List   | Prerequisites to be installed      | []
| docker_ce_package_name        | String | Package name                       | docker
| docker_ce_repo_name           | String | Repository name                    | docker-ce
| docker_ce_repo_url            | String | Repository URL                     | https://download.docker.com/linux/centos/docker-ce.repo
| docker_compose_package_name   | String | Package name for Docker Compose    | "docker-compose"
| docker_daemon_options         | Dict   | Docker Daemon options              | { debug: false }
| docker_install_docker_compose | Bool   | Should Docker Compose be installed | true
| docker_pip_package_name       | String | pip package name                   | python-pip
| docker_sdk_package_name       | String | Docker SDK package name            | docker
| docker_service_enabled        | Bool   | Should Docker service be enabled   | true
| docker_service_name           | String | Name of Docker service             | docker
| docker_storage_driver         | String | Storage Driver to use              | overlay2
| docker_users                  | List   | Users to put in group `docker`     | []

Dependencies
------------

No dependencies.

Example Playbook
----------------
```yaml
- name: Install Docker
  hosts: all
  become: true
  roles:
    - role: phrosenberg.docker
      vars:
        docker_users:
          - alice
          - grace
        docker_daemon_options:
          debug: false
          live-restore: true
```

License
-------

MIT

Author Information
------------------

Philip Rosenberg
philip@rosenberg.dev
