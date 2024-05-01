# Current Workflow
This is a my current workflow, with asdf, direnv, and poetry.

See my dotfiles for additional config.


## When starting a new project:
```zsh
# create repo
git init

# create .gitignore

# create .tool_versions
asdf local python latest

# initialise project
echo "layout poetry" > .envrc
direnv allow

# set up vscode settings and workspace
# cp -r .../current_workflow/.vscode .../{new_project}/.vscode
# mv .../current_workflow/current-workflow.code-workspace .../current_workflow/{new-project}.code-workspace

# install packages
poetry add pandas

# export requirements
# poetry export -f requirements.txt --output requirements.txt
```

## When working on an existing project:
```zsh
# clone repo
git clone https://...

# ... set up python environment as above

# install packages
poetry install

# update pip
pip install --upgrade pip

# make binaries accessible from PATH
asdf reshim python
```


# Poetry
To store virtual environments in the project's root directory:

```zsh
poetry config virtualenvs.in-project true
poetry config --list
```

### Example 1: Installing a local git repository with extras:
```zsh
git clone https://github.com/polakowo/vectorbt.pro.git

# pyproject.toml
# vectorbtpro = { path = “$HOME/Project/vectorbt.pro“, extras=[“base”], develop = true }
```

### Example 2: Installing a git repository with extras:
```zsh
poetry add "git+https://github.com/polakowo/vectorbt.pro.git[base]"

# pyproject.toml
# vectorbtpro = { git = "https://github.com/polakowo/vectorbt.pro.git", extras = ["base"] } 
```

# Pip
Useful commands when working with pip and poetry:

```zsh
# export dependencies to requirements.txt for Docker
poetry export --without-hashes --format=requirements.txt > requirements.txt

# uninstall everything
pip freeze | xargs pip uninstall -y
```


# References
1. GitHib (2023) A Collection of .gitignore Templates. Available at: https://github.com/github/gitignore (Accessed 13/10/2023).
2. Google (2023) Google Python Style Guide. Available at: https://google.github.io/styleguide/pyguide.html (Accessed 13/10/2023).
3. direnv (2023) poetry. Available at: https://github.com/direnv/direnv/wiki/Python#poetry (Accessed 13/10/2023).
