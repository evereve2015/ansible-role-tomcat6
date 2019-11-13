# Ansible Role: Tomcat 7

An Ansible Role that installs Tomcat 7 on RedHat/CentOS (and Debian/Ubuntu) Linux servers. This role, originated from geerlingguy's Tomcat6 role, was developed for XNAT.  

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    tomcat_enabled: true

Whether Tomcat 7 should be started at boot (as well as at the time this playbook is run). Set to false if you would like to leave Tomcat 7 installed but not running, or want to control it on your own.

    tomcat_server_port: 8005

The port on which the Tomcat 7 server itself will run (not the difference between this and the `tomcat_catalina_port`).

    tomcat_hostname: "{{ ansible_hostname }}"

The hostname for this server.

    tomcat_catalina_port: 8080

The port on which Catalina will listen for requests. (This is the port through which webapps will be accessible).

    tomcat_catalina_redirect_port: 8443

This is the port to which requests will be redirected if they come in on a non-SSL port, but are required to be secure via a security constraint.

## Dependencies

  - geerlingguy.java (Installs Java for CentOS).

## Example Playbook

    - hosts: webservers
      vars_files:
        - vars/main.yml
      roles:
        - { role: geerlingguy.tomcat }

*Inside `vars/main.yml`*:

    tomcat_hostname: example.com
    tomcat_catalina_port: 8080

## License

MIT / BSD

## Author Information

This role was updated in 2017 by Wally Chu @ Macquarie University. The original role was created in 2014 by [Jeff Geerling](https://www.jeffgeerling.com/), author of [Ansible for DevOps](https://www.ansiblefordevops.com/).

