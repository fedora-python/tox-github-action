![Run Tox tests](https://github.com/fedora-python/tox-github-action/workflows/Run%20Tox%20tests/badge.svg)
![Run tests with code in this repository](https://github.com/fedora-python/tox-github-action/workflows/Run%20tests%20with%20code%20in%20this%20repository/badge.svg)

# Tox Github Action

This GitHub action tests a checked-out Python project using
[Tox](https://tox.readthedocs.io/en/latest/index.html).


## Usage

```yaml
- uses: fedora-python/tox-github-action
  with:
    # The tox environment to run
    # Default: py38 (subject to change as new Python releases come out)
    tox_env: py38
```

Add the action to your workflow file, e.g. `.github/workflows/main.yml`,
after checking out your code.

You can use the `matrix` strategy to run with multiple Tox environments.
For an example, see [this project's workflow](.github/workflows/main.yml).
Unfortunately, you need to repeat all the environment names
from your Tox configuration.
(As far as we know, this is required in order to have individual environments
show up as separate runs on GitHub. Discuss this limitation in [issue 8].)

Similarly, you can run tox on multiple architectures:

```yaml
strategy:
  matrix:
    arch: [amd64, arm64, ppc64le, s390x]
...
- uses: fedora-python/tox-github-action
  with:
    tox_env: py38
    arch: ${{ matrix.arch }}
```

You can also install RPM packages from Fedora by setting `dnf_install` to
a space-separated list of *provides*, such as:

* Fedora package names, e.g. `libgit2-devel`,
* pkgconfig names, e.g. `pkgconfig(libffi)`,
* commands, e.g. `/usr/bin/cowsay`, ...

```yaml
- uses: fedora-python/tox-github-action
  with:
    tox_env: py38
    dnf_install: pkgconfig(libffi) libgit2-devel
```

The string will be literally used in `dnf install ...`, so you can also use
groups or DNF options.

[issue 8]: https://github.com/fedora-python/tox-github-action/issues/8

## License

The code, content and configuration in this repository is given away unter the
CC0 1.0 Universal Public Domain Dedication:
https://creativecommons.org/publicdomain/zero/1.0/

May it serve you well!
