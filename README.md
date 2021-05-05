# gh-tag-action

A composite Github Action to automatically bump and push semver tag.

It finds latest tag and creates and pushes new one based on found one
bumping  major/minor/patch accoring to provided config. Default is minor.

It works with an assumption `actions/checkout@v2` is executed first in
a workflow.

The action generates `new-version` output with a value for a new tag.


# Usage

<!-- start usage -->
```yaml
- uses: figment-networks/gh-tag-action@v0.1.0
  with:
    # Which part of semver to bump for latest tag (major/minor/patch)
    # Default: minor
    default-bump: ''

```
<!-- end usage -->

# Scenarios

- [Generate and push a new tag with minor part bumped](#Generate-and-push-a-new-tag-with-minor-part-bumped)
- [Generate and push a new tag with patch part bumped](#Generate-and-push-a-new-tag-with-patch-part-bumped)

## Generate and push a new tag with minor part bumped

```yaml
- uses: actions/checkout@v2
- name: Bump version and push tag
  id: tag-version
  uses: figment-networks/gh-tag-action@0.1.0
- name: debug
  run: echo ${{ steps.tag-version.outputs.new-version }}
```

## Generate and push a new tag with patch part bumped

```yaml
- uses: actions/checkout@v2
- name: Bump version and push tag
  id: tag-version
  uses: figment-networks/gh-tag-action@0.1.0
  with:
    default-bump: patch
- name: debug
  run: echo ${{ steps.tag-version.outputs.new-version }}
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)
