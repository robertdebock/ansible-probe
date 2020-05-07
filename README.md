Ansible Probe
=============

Use molecule with many distributions to update the `platforms` section in `meta/main.yml`.

Usage
-----

1. Edit `combinations.yml`

This file lists all combinations that should be tried.

An example of `combinations.yml`:

```yaml
---
images:
  - name: opensuse
    # The list of `tags` is set to `['latest']` when not specified.
  - name: fedora
    tags:
      - 31
      - latest
      - rawhide
```

2. Go to the directory where your role lives:

```
$ cd /my/homedir/ansible-role-my_role
```

3. Run `probe.yml`

```
./probe.yml
```

4. The results are saved in `~/output/{{ role_name }}-(un)successful.txt`, for example:

```
$ cat /tmp/my_role-successful.txt
image=opensuse tag=latest
image=ubuntu tag=latest
image=ubuntu tag=rolling
image=ubuntu tag=devel
```

5. Verify meta.yml

Open `meta/main.yml` and see that `platforms` has been updated with succesfully tested platforms.

Output
------

There are a few interesting files:

- {{ role_name }}/* - Parts used to generate {{ role_name }}-meta.yml.
- {{ role_name }}-meta.yml - The part that can be used in `meta/main.yml`.
- {{ role_name }}-{{ image.name }}-{{ tag }}.txt - The output of molecule runs.to try and how to map images to Ansible Galaxy platforms:

- `data/combinations.yml` is a list of images and tags to try.
- `data/{{ image.name }}.yml`

Data
----

There are a few files that help to determine what to try and how to map images to Ansible Galaxy platforms:

- `data/combinations.yml` is a list of images and tags to try.
- `data/image_galaxy_platform.yml` is a list of images and their relation to Ansible Galaxy platforms.
- `data/{{ image.name }}.yml` are files (per image name) to map container tags to Ansible Galaxy platform versions.
