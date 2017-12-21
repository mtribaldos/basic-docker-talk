# Ansible for Pythonistas

#### Python Valencia Meetup
##### November 2017

<div align="left">
<small>
Miguel Ángel Tribaldos  
Senior Developer  
@mtribaldos
</small>
</div>

---

### I've just coded my app. Now what?

## Time to ship it, but...

- Provision infrastructure
- Manage configuration
- Deploy application

---

### Is there a better way than doing by hand?

- Avoid repeating manual work
- Ability to reset and reconfigure infrastructure
- Visibility

+++

## Infrastructure and
## Configuration
## as Code

---

##### The simple approach
### Shell scripts

- Not robust, bad maintenance
- Explicit transport mechanisms. Non-standard methods
- Hard to achieve reusable code

+++

### They end up being use and throw artifacts!

---

##### The pythonic approach
### What about Fabric?

- Writing infrastructure code in Python
- Fine for deployment tool, not for CM
- Suitable for small environments

```python
# ~/fabfile.py

from fabric.api import *

env.hosts = ['test.example.org']
env.user  = 'bob'

def remote_info():
    run('uname -a')

def local_info():
    local('uname -a')
```
