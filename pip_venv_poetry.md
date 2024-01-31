### Poetry command
````bash
poetry
````
````bash
poetry env list
````
````bash
poetry env info --path
````
see poetry config list.

````bash
poetry config --list
````
output : 
```bash
cache-dir = "/home/mhabib/.cache/pypoetry"
experimental.system-git-client = false
installer.max-workers = null
installer.modern-installation = true
installer.no-binary = null
installer.parallel = true
virtualenvs.create = true
virtualenvs.in-project = null
virtualenvs.options.always-copy = false
virtualenvs.options.no-pip = false
virtualenvs.options.no-setuptools = false
virtualenvs.options.system-site-packages = false
virtualenvs.path = "{cache-dir}/virtualenvs"  # /home/mhabib/.cache/pypoetry/virtualenvs
virtualenvs.prefer-active-python = false
virtualenvs.prompt = "{project_name}-py{python_version}"
warnings.export = true
```
set virtualenvs.in-project true 
```bash
poetry config virtualenvs.in-project true
poetry config virtualenvs.prefer-active-python true
```

````bash
pyenv
```
see all python version with 3.10

```bash
pyenv install --list | grep 3.10
```
install another version of python besides global python
```bash
pyenv install 3.10.13
```
To see all available python versions
```bash
pyenv versions
```
If you run "python -V" you will see global python version. which is python 3.12 but in our project we need 3.10. how we can solve it. now we can set local python version
```bash
pyenv local 3.10.13
pyenv local
```
Now we set local python version and global python version. if you run "python -V" in your project dir you will see local python version 3.10 but if you run "python -V" from outside this project dir you will see 3.12

```bash
poetry instal
```
To see which python path we are using
```bash
which python
```
To see global and local python versions
```
pyenv global
pyenv local
```
```bash
poetry shell
```
To go inside poetry venv

```bash
. /home/mhabib/projects/diagnose-portal/diagnose-api/.venv/bin/activate
```
To run this project 
```bash
python src/main.py --reload --port 8081
```
Or direcktly from outside project dir
```bash
poetry run python src/main.py --reload --port 8081
```