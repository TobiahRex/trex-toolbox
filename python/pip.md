# [Home](../README.md) > PIP tools
[Home](../README.md)

1. Create a virtual environment with Python 3.11
   ```bash
   virtualenv -p python3.11 venv
   # This installs a specific Python version inside the virtual environment.
   ```

2. Install project dependencies
   ```bash
   pip install --force-reinstall -e .
   # Requites a setup.py file in the project root.
   ```
   or
    ```bash
    pip install -r requirements.txt
    # Requires a requirements.txt file in the project root.
    ```

3. Upgrade python-dev-tools package
   ```bash
   python -m pip install python-dev-tools --user --upgrade
   ```

4. Upgrade pip version
   ```bash
   python -m pip install --upgrade pip==19.3
   # This changes the active version of pip used for "pip install".
   ```

5. Installing Virtual Env per Project
   - Download direnv
   - Create a .envrc file in the root project directory with the following contents:
     ```bash
     export VIRTUAL_ENV=.env
     layout python-venv python3.11
     ```

6. Install local/remote repo as a pip package
    ```bash
    pip uninstall <package>
    pip install -e git+https://github.com/yewno/yttrium.git@<commit>#egg=<package/repo>
    # Replace <package> with the name of the package you want to install.
    # Replace <commit> with the commit hash of the repo you want to install.
    # Replace <package/repo> with the name of the package/repo you want to install.
    ```