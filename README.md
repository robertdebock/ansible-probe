Ansible Probe
=============

Run molecule on many combinations to generate a list of working (and not working) combinations.

Usage
-----

1. Edit `combinations.yml`

An example of `combinations.yml`:

```yaml
---
images:
  - name: opensuse
    # The list of `tags` is set to `['latest']` when not specified.
  - name: ubuntu
    tags:
      - latest
      - rolling
      - devel
```

2. Go to the directory where your role lives:

```
$ cd /my/homedir/ansible-role-my_role
```

3. Run `playbook.yml`

```
./playbook.yml
```

4. The results are saved in `~/output/{{ role_name }}-(un)successful.txt`, for example:

```
$ cat /tmp/my_role-successful.txt
image=opensuse tag=latest
image=ubuntu tag=latest
image=ubuntu tag=rolling
image=ubuntu tag=devel
```

The output of the job runs is saved in `~/output/{{ role-name }}-{{ image }}-{{ tag }}.txt`
