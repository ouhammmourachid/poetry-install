# poetry-install

This repository demonstrates how to use GitHub Actions to set up Python, install Poetry, and install project dependencies.

- `python-version`: This variable specifies the version of Python that will be set up in the workflow. It is used with the actions/setup-python@v3 action to configure the Python environment default `3.10`.

- `poetry-version`: this variable used to specify the version of Poetry that will be installed. The snok/install-poetry@v1 action is used to install Poetry default `latest`.

- `extra-args`: this variable used to set the extra args for the `poetry install` command .

- `install-dependencies`: default `true` used to install the dependencies. set it to `false` if you don't want to install the dependencies.

## Workflow

The workflow is triggered on every push to the repository. It performs the following steps:

1. Sets up the Python version specified with `actions/setup-python@v3`.
2. Installs Poetry using `snok/install-poetry@v1`.
3. Installs project dependencies using Poetry.

## Usage

To use this workflow in your own repo you should have `pyproject.toml` file and then write a workflow like this one.

```yml
name: poetry install

on:
  workflow_dispatch

jobs:
  install-dependecies:
    runs-on: ubuntu-latest
    steps:
      - name: checout
        uses: actions/checkout@v4
      - name: install dependecies
        uses: ouhammmourachid/poetry-install@v2.0.0
      - name: test
        run: poetry show --tree

```
