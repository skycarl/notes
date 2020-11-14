# Google Colab notes

## Authenticating to GitHub to access a private repo

```python
import os
from getpass import getpass
import urllib

user = input('User name: ')
password = getpass('Password: ')
password = urllib.parse.quote(password) # your password is converted into url format
repo_name = input('Repo name: ')

cmd_string = 'git clone https://{0}:{1}@github.com/{0}/{2}.git'.format(user, password, repo_name)

os.system(cmd_string)
cmd_string, password = "", "" # removing the password from the variable
```

Note that if 2FA is enabled, an access token is needed instead of a password. `repo` permissions appear to work when generating the token. 

Source: https://stackoverflow.com/questions/48350226/methods-for-using-git-with-google-colab

## File navigation

For traversing directories in Colab, use `%` rather than `!`; e.g. `%cd dir_name/`
