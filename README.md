# DevSecOps Lab: DHCP & DNS (Rocky Linux 9)

Infraestructura como Código (IaC) para desplegar servicios base de red utilizando Ansible y Vagrant.

## Tecnologías
* **OS:** Rocky Linux 9
* **Provisión:** Ansible (`ansible.builtin` + `ansible.posix`)
* **Entorno:** Vagrant (VirtualBox)
* **CI/CD:** GitHub Actions (Lint, Syntax, preparativo para Molecule)

## Uso Rápido
1. Iniciar la infraestructura: `vagrant up`
2. El servidor se aprovisionará automáticamente.
3. Entrar al cliente para validar: `vagrant ssh client` y ejecutar `./client_test.sh`.