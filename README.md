This repository contains an [Ansible](http://www.ansible.com/) playbook
to create machines in [Digital Ocean](https://www.digitalocean.com/) and
add entries for each to DNS using the [DNSimple](http://dnsimple.com) API.

## Usage

Note that this assumes you have a DigitalOcean and DNSimple account and
have the relevant values stored in the following environment variable:
`DO_CLIENT_ID`, `DO_API_KEY`, `DNSIMPLE_EMAIL` and `DNSIMPLE_API_TOKEN`.

```bash
ansible-playbook -i hosts provision.yml
```

The specific code here has a few hardcoded elements that you'll likely
want to change for your own usage.

## Generating configuration

A small script is provided to generate random names for use in
provisioning machines. The names are used as both the name of the
instance and as the subdomain so need a good degree of uniqueness.

```bash
go run printnames.go <number>
```

This will print a YAML formatted configuration file for use by ansible.
You'll probably run something like:

```bash
go run printnames.go 200 > vars/droplets.yml
```

