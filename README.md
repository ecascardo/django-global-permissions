# Django Global Permissions

Implementation of permissions not related to models

# Quickstart

Install django-global-permissions:

```
pip install django-global-permissions
```

Add to the installed apps:

```python
INSTALLED_APPS += (global_permissions,)
```

If you want co create a permission in the admin interface, then head to
the Global Permissions section, then add a permission. Pick a name (which
should be a human readable description), a code name (which will be used throughout
the your apps), then save it.

Then open the user edit page. Now you can choose the permission you've just created.

Otherwise if you want to create a permission programmatically, just import the GlobalPermission
model and create a new permission choosing a name and a codename.

```python
from global_permissions.models import GlobalPermission

GlobalPermission.objects.create(name='My Perm', codename='my_perm')
```

## Putting into action!

Lets say you want to verify if the logged in user can do something (based on a permission).
In your view, you can do the following

```python
if user.has_perm('global_permissions.my_perm_codename'):
    pass # do something intersting!
else:
    pass # ops, you're not allowed to do that. Sorry ¯\_(ツ)_/¯
```

If you cant to verify a permission inside some template, you can do this way:

```htmldjango
{% if perms.global_permissions.my_perm_codename %}
    Yay!
{% else %}
    Not so lucky...
{% endif %}
```
