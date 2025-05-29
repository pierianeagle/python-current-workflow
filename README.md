# Current Workflow
This is a my current workflow, with ~~asdf, direnv, and poetry~~ uv!

Please see my dotfiles for additional config.


## When starting a new project:
```zsh
# create repo
uv init

# replace .gitignore

# optionally set up environment variables
echo "export API_KEY=123" > .envrc
direnv allow

# set up vscode settings and workspace
# cp -r .../current_workflow/.vscode .../{new_project}/.vscode
# mv .../current_workflow/current-workflow.code-workspace .../current_workflow/{new-project}.code-workspace

# install packages
uv add pandas
uv add --group dev ruff

# optionally install this package as editable
uv pip install -e .
```

## When working on an existing project:
```zsh
# clone repo
git clone https://...

# install packages
uv sync --all-groups

# optionally upgrade pip
pip install --upgrade pip
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
uv pip freeze > requirements.txt

# uninstall everything
pip freeze | xargs pip uninstall -y
```


# References
1. GitHib (2023) A Collection of .gitignore Templates. Available at: https://github.com/github/gitignore (Accessed 13/10/2023).
2. Google (2023) Google Python Style Guide. Available at: https://google.github.io/styleguide/pyguide.html (Accessed 13/10/2023).
3. direnv (2023) poetry. Available at: https://github.com/direnv/direnv/wiki/Python#poetry (Accessed 13/10/2023).
4. astral (2025) Working on projects. Available at https://docs.astral.sh/uv/guides/projects/ (Accessed 29/05/2025).
5. direnv (2025) GitHub Issue #1250. Available at: https://github.com/direnv/direnv/issues/1250 (Accessed 29/05/2025).
