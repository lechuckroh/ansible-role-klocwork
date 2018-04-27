# Ansible role `klocwork`

An ansible role for installing Klocwork.

Tested under:
* CentOS 7.4
* Ubuntu 16.04
* Ubuntu 18.04

## Requirements

No requirements

## Role Variables

| Variable                    | Default               | Comments                       |
|:----------------------------|:----------------------|:-------------------------------|
| `klocwork_user`             | `klocwork`            | Remote host klocwork run user. Creates user if not exists |
| `klocwork_dir`              | `/opt/tools/klocwork` | Remote host klocwork installation directory |
| `klocwork_script_dir`       | `/home/klocwork`      | Remote host directory to create scripts for service start/stop |
| `klocwork_installer_src`    |         | Klocwork installer path. (**required**) |
| `klocwork_installer_dest`   | `/tmp`  | Remote host directory to store klocwork installer |
| `klocwork_license_fileglob` | `*.lic` | Klocwork license filenames to use |
| `klocwork_start_service`    | `false` | Set `true` to start klocwork service after installation finished. |
| `klocwork_port_database`    | `3306`  | Database server port |
| `klocwork_port_web`         | `8080`  | Klocwork server port |
| `klocwork_port_license`     | `27000` | LicenseServer server port. |

## Dependencies

No dependencies

## Example Playbook

```yaml
---
- name: example
  hosts: all
  become: true
  vars:
    klocwork_installer_src: ./klocwork/kw-server-installer.18.0.0.939.linux64.sh
    klocwork_license_fileglob: ./klocwork/*.lic
    klocwork_start_service: true
  roles:
  - lechuckroh.klocwork
```

1. After klocwork service is started, open `http://<host>:8080`
2. Login as :
  * username: value of `klocwork_user` (default value:  `klocwork`)
  * password: empty

## License
MIT
