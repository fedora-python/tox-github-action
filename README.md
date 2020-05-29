![Tox sanity test](https://github.com/encukou/tox-github-action/workflows/Tox%20sanity%20test/badge.svg)

# Tox Github Action

This GitHub action tests a checked-out Python project using
[Tox](https://tox.readthedocs.io/en/latest/index.html).


## Usage

```yaml
- uses: encukou/tox-github-action
  with:
    # The tox environment to run
    # Default: py38 (subject to change as new Python releases come out)
    tox_env: py38
```

Add the action to your workflow file, e.g. `.github/workflows/main.yml`,
after checking out your code.

You can use the `matrix` strategy to run with multiple Tox environments.

For an example, see [this project's workflow](.github/workflows/main.yml).
