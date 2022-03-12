# install-opendylan

A GitHub Action to install the Open Dylan compiler.

To install the latest Open Dylan release on Linux or macOS (Windows not yet
supported):

```yaml
    - uses: dylan-lang/install-opendylan@v2
```

To install a specific released version:

```yaml
    - uses: dylan-lang/install-opendylan@v2
      with:
        version: 2020.1
        tag: v2020.1.0
```

`version` is the version number used in the top-level Open Dylan directory when
unpacked from the tarball.

`tag` is the exact tag identifying the GitHub release, including the leading
"v".

**Important:** This Action must be used **after**
[actions/checkout@v2](https://github.com/actions/checkout) when using the
default `path:` (i.e., the current directory) because `actions/checkout@v2`
deletes everything in the repo directory first.

When this Action has completed two artifacts exist in the current directory:

1.  A symbolic link to the `dylan-compiler` executable.

2.  A symbolic link named `opendylan` that points to the Open Dylan
    installation directory.

See the [hello](https://github.com/cgay/hello) repository for the canonical
example of how to use this Action.
