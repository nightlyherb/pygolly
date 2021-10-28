# Python bindings for Golly

## About

Currently Golly _embeds_ a Python interpreter for executing script code.
This is why the `golly` module is only available _inside_ Golly.
This prevents writing Golly scripts _outside_ of Golly.
This may be fine for writing small one-off scripts,
but doesn't really scale when your script gets longer than a single page/file.

This package implements Python scripting the other way around:
it _extends_ Python with Golly and loads it from Python.
You can use your normal Python development workflow with your favorite IDE.
No more `module "golly" is not defined` errors. Say hi to testing.

The author intends to support Jupyter notebooks as well.
(TODO: IPython/Jupyter bindings)

## Differences from Golly scripting

Scripting

## Setup

1. Install pdm (See [pdm docs](https://pdm.fming.dev))

1. Initialize repo and setup project

   ```sh
   git clone https://github.com/NightlyHerb/pygolly --recurse-submodules
   pdm update
   ```

1. For `vscode` users:
   Set your Python include path
   to the environment variable `PYGOLLY_PYTHON_INCLUDE`
   in order to find `<Python.h>`.

## Structure

- `/golly` submodule: Has the upstream Golly code
- `/pygolly-cpp`: The C++ glue code
- `/pygolly`: The Python glue code
- `/tests`: tests

## Tools used

The formatters/tests are executed on pre-commit via git hooks.

### Python

- [![Code style: black](https://img.shields.io/badge/code_style-black-black)](https://github.com/psf/black)
- [![Tests: pytest](https://img.shields.io/badge/tests-pytest-blue)](https://pytest.org)
- [![pdm-managed](https://img.shields.io/badge/pdm-managed-blueviolet)](https://pdm.fming.dev)
### Markdown

- [![Code style: mdformat](https://img.shields.io/badge/code_style-mdformat-0000ff)](https://github.com/executablebooks/mdformat)

  - TBH I don't like the 3-space hanging indents of ordered lists,
    but I can see it's the best we have now and I can take it.

- [![Code style: Semantic linefeeds](https://img.shields.io/badge/code_style-semantic_linefeeds-default)][link-sem-lf]

  - In order to minimize diff size, markdown prose is broken down into lines via
    [semantic linefeeds][link-sem-lf].
  - I did merge multiple phrases into one line
    iff the sentences are related and there is line estate.

[link-sem-lf]: https://rhodesmill.org/brandon/2012/one-sentence-per-line/
