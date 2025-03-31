[![tests](https://github.com/dylan-lang/install-opendylan/actions/workflows/build-and-test.yml/badge.svg)](https://github.com/dylan-lang/install-opendylan/actions/workflows/build-and-test.yml)

# install-opendylan

A GitHub Action to install the Open Dylan compiler (`dylan-compiler`) and
`dylan` tool.

To install the latest Open Dylan release on Linux or macOS (Windows not yet
supported):

```yaml
    - uses: dylan-lang/install-opendylan@v3
```

To install a specific released version:

```yaml
    - uses: dylan-lang/install-opendylan@v3
      with:
        tag: v2020.1.0
```

`tag` is the exact tag identifying the GitHub release, including the leading
"v".

**Important:** This Action must be used **after**
[actions/checkout@vN](https://github.com/actions/checkout) when using the
default `path:` (i.e., the current directory) because `actions/checkout@v2`
deletes everything in the repo directory first.

When this Action has completed the following artifacts exist:

1.  A directory containing the `dylan-compiler` and `dylan` executable binaries
    has been added to the `PATH`.

3.  `${GITHUB_WORKSPACE}/../opendylan` is a symbolic link pointing to the Open
    Dylan installation directory.

**Note:** Files are installed outside of `${GITHUB_WORKSPACE}` so that they
won't be deleted by the "checkout" GitHub action and so that they aren't
included by the `dylan update` command when generating registry files.

See the [hello](https://github.com/cgay/hello) repository for the canonical
example of how to use this Action.

# Versions

This repository uses standard [Semantic Versioning](https://semver.org), but also
provides moving tags for each major version for those who want to get the latest Open
Dylan releases automatically. For example, the "v3" tag always points to the latest
release with major version 3, e.g., `v3 -> v3.2.1`.  The major version of
`install-opendylan` only changes when the Action itself is changed incompatibly, as with
normal SemVer semantics.
