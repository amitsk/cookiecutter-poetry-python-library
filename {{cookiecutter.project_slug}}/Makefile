
.PHONY: clean clean-test clean-pyc clean-build docs help
.DEFAULT_GOAL := help
BASE := $(shell /bin/pwd)
CODE_COVERAGE = 50
POETRY ?= poetry

build: install test coverage lint

install:
	$(info [*] Installing POETRY project dependencies)
	@$(POETRY) install
	

shell:
	@$(POETRY) shell

help:
	@python -c "$$PRINT_HELP_PYSCRIPT" < $(MAKEFILE_LIST)

clean: clean-build clean-pyc clean-test ## remove all build, test, coverage and Python artifacts

clean-build: ## remove build artifacts
	rm -fr build/
	rm -fr dist/
	rm -fr .eggs/
	find . -name '*.egg-info' -exec rm -fr {} +
	find . -name '*.egg' -exec rm -f {} +
	find . -name '*.dist-info' -exec rm -fr {} +
clean-pyc: ## remove Python file artifacts
	find . -name '*.pyc' -exec rm -f {} +
	find . -name '*.pyo' -exec rm -f {} +
	find . -name '*~' -exec rm -f {} +
	find . -name '__pycache__' -exec rm -fr {} +

clean-test: ## remove test and coverage artifacts
	rm -fr .tox/
	rm -f .coverage
	rm -fr htmlcov/
	rm -fr .pytest_cache

lint: ## Check code with pyflakes and mypy ( errors ignored)
	@$(POETRY) 	run pyflakes {{cookiecutter.project_module}}
	-@$(POETRY) run mypy  {{cookiecutter.project_module}}

test: ## run tests quickly with the default Python
	@$(POETRY) run python -m pytest --cov . --cov-report term-missing --cov-fail-under $(CODE_COVERAGE)  tests/ -v


coverage: ## check code coverage quickly with the default Python
	coverage run --source {{ cookiecutter.project_module }} -m pytest
	coverage report -m
	coverage html


