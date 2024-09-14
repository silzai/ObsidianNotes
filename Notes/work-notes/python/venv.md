# create venv
```sh
python3 -m venv env
# env is the environment name
```
# to activate the venv
```sh
source env/bin/activate
```
# to add packages to the venv
```
pip3 install packagename
```
# to save all packages installed to a venv
```shell
pip freeze > requirements.txt
```
# to install packages from requirements.txt
```sh
pip install -r requirements.txt
```
