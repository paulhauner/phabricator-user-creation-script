# phabricator-user-creation-script

A PHP script which allows the creation of a single Phabricator user by supplying parameters on script runtime. This is easier to call programmatically than Phabricator's interactive `bin/accountadmin` script.

This was directly adapted from Phabricator's `bin/accountadmin` script.

## Usage

This script must run on your Phabricator host. It utilises the `phabricator/scripts/__init_script__.php` to actually carry out operations on Phabricator.

This script assumes your Phabricator instance is located at `/opt/phabricator`. If this isn't the case, you can simply change the `require_once '/opt/phabricator/scripts/__init_script__.php';` line to point to wherever you need.

To run from `bash`:
````
$ ./create_users.php "newusername" "newpassword" "Mr New Pants" "new_guy12@hotmail.com"
````

In my case, I wanted to execute this script in Python. Python example:
````
import os
from subprocess import Popen

PHP_SCRIPT = os.path.join(os.path.dirname(os.path.realpath(__file__)), "create_user.php")

process = Popen([PHP_SCRIPT, "newusername", "newpassword", "Mr New Pants", "new_guy12@hotmail.com"])
process.wait()
print(process.returncode)
````

## Contribution

Feel free to contribute!
