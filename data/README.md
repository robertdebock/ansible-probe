# combinations.yml

This file tells ansible-probe what combinations of distribution and version to try.

- The `name:` (string) refers to the Docker container name.
- The `tags:` (list) refers to the tags of that Docker container.

```yaml
---
images:
  - name: x
    tags:
      - y
      - z
```

# x.yml

You need to futher instruct ansible-probe how `x`'s versions relate to [Ansible Galaxy platform version](https://galaxy.ansible.com/api/v1/platforms/) of that distribution.

```yaml
---
_galaxy_version:
  7: 7
  latest: 8
```

- `7: 7` is a one to one mapping; the Docker container tag (left) is similar to the Ansible Galaxy version. (right)
- `latest: 8` maps the Docker container tag `latest` to the Ansible Galaxy version `8`.
