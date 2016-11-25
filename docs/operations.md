
### Locations

am1: pcextreme Amsterdam East
am2: pcextreme Amsterdam West

Location names should start at 1


### Naming

```sh
$server.$location.$project.infra.nlnog.net
```

Server names should start at 0 and go up across locations.


### Development machines

- ans0.am1.dev.infra.nlnog.net

CentOS-7

- ans1.am2.dev.infra.nlnog.net

Debian-8

- ans2.am1.dev.infra.nlnog.net

Ubuntu-12.04


### Using molecule

Spin up containers and run all tests with:

```sh
molecule test
```

Run only `ansible-playbook` command

```sh
molecule converge
```

Run only the tests

```sh
molecule verify
```

Turn off all molecule docker containers

```sh
molecule destroy
```


### Troubleshooting molecule


Run with the `--debug` flag to get the commands, then modify to something like

```sh
ANSIBLE_KEEP_REMOTE_FILES=1 ansible-playbook site.yml --inventory-file=.molecule/ansible_inventory --sudo --vault-password-file=/dev/null --connection=docker --user=root --timeout=30 --diff -vvvv --limit=infra-ubuntu-12.04
```

To run the tests directly to docker without cycling molecule:

```sh
testinfra --debug --connection=docker tests/
```

Run the linter alone:

```sh
ansible-lint playbook.yml --exclude .git --exclude .vagrant --exclude .molecule
```
