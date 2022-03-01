# install-opendylan

A GitHub Action to install the Open Dylan compiler.

Example:

```yaml
    - uses: dylan-lang/install-opendylan@v1
      with:
        version: 2020.1
```

The version is optional and will generally default to the latest release.

Complete job example using the `strings` library:

```yaml
jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: dylan-lang/install-opendylan@v1

      - name: Build strings-test-suite
        run: ./dylan-compiler -build -jobs 3 strings-test-suite

      - name: Run strings-test-suite
        run: _build/bin/strings-test-suite
```

When this Action has completed two artifacts exist at the top-level in your
GitHub workspace:

1.  A symbolic link named `opendylan` that points to the Open Dylan
    installation directory.

2.  A link to the `dylan-compiler` binary.
