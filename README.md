# Welcome to Ansible examples by OpenTable!

Please check out our SF Ansiblefest 2017 presentation [here](Ansiblefest2017/Ansiblefest_2017_OT.pdf)

## Interactive play with examples
If you wish to have hands-on experience with all examples and code fragments available in this repo, you may want to build python virtual environment by following those steps:
- sudo pip install virtualenv
- virtualenv --no-site-packages venv
- source venv/bin/activate
- pip install -r requirements.txt
- ansible-galaxy install -r requirements.yaml

Then you should be able to run ansible-playbook command like this:
```
ansible-playbook playbooks/example.yaml
```
which will give you a list of examples that you may execute and see what they produce (and examine their code, if interested).
```
TASK [describe_examples : Display short descriptions for each category] ***********************************************************************************************
skipping: [test]
ok: [help] => {
    "changed": false, 
    "msg": [
        "builtin_filters      - Ansible builtin filters and extra filters installed via pip requirements.txt", 
        "custom_filters       - Custom python filters we built ourselves to extend Ansible "
    ]
}
```
## Start local webserver to support dynamic inventory
The next step (after you see a list of examples' groups available from previous command)
would be to start a local web server that will support Ansible dynamic
inventory. For that you would need to run command similar to this:
```
webserver/webserver.rb  2> /dev/null &
```

Now each example group (a folder on a local file system) would be
addressable via "-l" argument of ansible-playbook command:
```
ansible-playbook playbooks/example.yaml -l builtin_filters
```
