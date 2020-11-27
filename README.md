# Debugging and Setting Up Jupyter Notebooks on Mac OS Within VSCode

- [Setting Up The Environment](#setting-up-the-environment)
- [Using Virtual Environments in Jupyter Notebook and Python](#using-virtual-environments-in-jupyter-notebook-and-python)
    + [Create Virtual Environment with Virtualenv/venv](#create-virtual-environment-with-virtualenv-venv)
- [Handling Dependencies, Collaboration and Github](#handling-dependencies--collaboration-and-github)

# Setting Up The Environment

We want to standarize which versions of Python we're running, we can do that using `pyenv`. 

1. Install Homebrew
```
xcode-select --install
xcode-select -p
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

2. Install Pyenv, a tool that allows you to specify which Python version you want to use:
```
brew update && brew doctor
brew install pyenv
export PYTHON_BUILD_HOMEBREW_OPENSSL_FORMULA=openssl@1.0
pyenv install 3.4.4
```

3. Verify version was installed 
`pyenv versions` and verify `3.4.4` is present in the list

4. Configure Bash Profile
`echo 'eval "$(pyenv init -)"' >> ~/.bash_profile`

5. Set the Python version globally on the system
`pyenv global 3.4.4`

6. Download VSCode from `https://code.visualstudio.com/`

7. Install the `Jupyter` VSCode extension by searching with (⇧⌘P) and typing `Install extension`

8. Install NBConvert for debugging purposes `pip3 install nbconvert`

Now you're ready to start using VSCode and Jupyter together to debug and build notebooks easily.


# Using Virtual Environments in Jupyter Notebook and Python

> A virtual environment is an isolated working copy of Python. This means that each environment can have its own dependencies or even its own Python versions. This is useful if you need different versions of Python or packages for different projects. This also keeps things tidy when testing packages and making sure your main Python installation stays healthy.


### Create Virtual Environment with Virtualenv/venv

Let's setup a new isolated virtual environment for our Jupyter notebook to ensure we don't have library or version conflicts with our dependencies.

1. Install virtualenv dependencies (you should only have to run this once forever)
```
pip3 install virtualenv
```

2. Setup a new virtualenv and install the kernel (you would do this for every project you want to have)
```
virtualenv jupyterenv
source jupyterenv/bin/activate 
pip3 install ipykernel
```

3. Verify you're running within the virtual environment like so: `pip -V`

# Handling Dependencies, Collaboration and Github

### Install sample dependencies inside of virtual environment

```
pip install -r reqs.txt
```