# VirtualEnv
Virtualenvs allow you to isolate your python packages between projects. They allow virtual isolation of projects so that python packages installed in one project's virtualenv doesn't affect the packages installed in another one.

How to run
```sh
$ virtualenv --no-site-packages env
$ source env/bin/activate
$ pip install ...
```