# {{cookiecutter.project_slug}}

![Run Tests and Lint](https://github.com/{{cookiecutter.project_slug}}/workflows/Run%20Tests%20and%20Lint/badge.svg)

- Poetry for dependency management
- Ruff for Linting
- Pytest for Unit tests and code coverage
- Mypy for type checking

## Building

- Install Python3.x ( Version selected during generation)
- Install poetry https://python-poetry.org/
- Clone from GitHub
- Install, test, lint `make install && make check`
- Tests can be run with `make test`
