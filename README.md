# install-opendylan

A GitHub Action to install the Open Dylan compiler.

To install the latest Open Dylan release on Linux or macOS (Windows not yet
supported):

```yaml
    - uses: dylan-lang/install-opendylan@v3
```

To install a specific released version:

```yaml
    - uses: dylan-lang/install-opendylan@v3
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

When this Action has completed the following artifacts exist:

1.  `${GITHUB_WORKSPACE}/../dylan-compiler` - the Open Dylan compiler.

2.  `${GITHUB_WORKSPACE}/../dylan` - the "dylan-tool" executable.

3.  `${GITHUB_WORKSPACE}/../opendylan` - a symbolic link pointing to the Open
    Dylan installation directory.

**Note:** The above files can usually be referenced simply as `../dylan` et
al. They are installed outside of `${GITHUB_WORKSPACE}` so that they don't get
deleted by the "checkout" GitHub action and so that they aren't included by the
`dylan update` command when generating registry files.

See the [hello](https://github.com/cgay/hello) repository for the canonical
example of how to use this Action.
