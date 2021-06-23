# role-symlinks

### Master:
[![role-symlinks](https://github.com/osx-provisioner/role-symlinks/actions/workflows/push.yml/badge.svg?branch=master)](https://github.com/osx-provisioner/role-symlinks/actions/workflows/push.yml)

### Production:
[![role-symlinks](https://github.com/osx-provisioner/role-symlinks/actions/workflows/push.yml/badge.svg?branch=production)](https://github.com/osx-provisioner/role-symlinks/actions/workflows/push.yml)

Ansible role that creates the configured symlinks.

Requirements
------------

None


Role Variables
--------------

Each symlink can be specified in the following format:

```yaml
symlinks:
  - link: /Users/{{ ansible_user_id }}/iCloud
    target: /Users/{{ ansible_user_id }}/Library/Mobile Documents/com~apple~CloudDocs
  - link: /Users/{{ ansible_user_id }}/workspace
    target: /Volumes/Code/
```

The following variables are also configured:

- `symlinks_user`:
    - The user to write the symlinks with.
- `symlinks_ignore_errors`:
    - A boolean indicating if errors should be ignored during symlink creation.

[See The Default Values](defaults/main.yml)

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: web
  roles:
  - role: osx_provisioner.symlinks
    symlinks_user: "{{ ansible_user_id }}"
    symlinks:
      - link: /Users/{{ symlinks_user }}/iCloud
        target: /Users/{{ symlinks_user }}/Library/Mobile Documents/com~apple~CloudDocs
      - link: /Users/{{ symlinks_user }}/workspace
        target: /Volumes/Code/
```

License
-------

MIT

Author Information
------------------

Niall Byrne <niall@niallbyrne.ca>
