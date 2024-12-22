# ndkprd's actions

A centralized collection of my personal Github/Gitea actions.

## ansible-release-to-galaxy

### Description

Github/Gitea Action to release [Ansible](https://ansible.com/) role to [Ansible Galaxy](https://galaxy.ansible.com).

What it does:
- do `git checkout`;
- use `ref_name` (usually from tag) to generate release;
- import the role to Ansible Galaxy via CLI.

### Usage

```yaml

name: Release.
on:
  push:
    tags:
      - 'v*'

jobs:
  release-to-galaxy:
    runs-on: ubuntu-latest
    steps:
      - name: Release to Ansible Galaxy.
        uses: ndkprd/actions/ansible/ansible-release-to-galaxy.yaml@main
        with:
          release_tag: ${{ github.ref_name }}
        secrets:
          galaxy_api_key: ${{ secrets.GALAXY_API_KEY }}

```

## License

[MIT](./LICENSE)
