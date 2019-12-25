# Reset Admin Password
------

In case you forget administrator password and are locked out of the system, you can run below command in [maintenance mode](maintenance-mode.md) to reset administrator password (assume OneDev is installed in _/opt/onedev_)
```
/opt/onedev/bin/reset_admin_password.(sh|bat) ${new-password}
```
Here _${new-password}_ should be replaced with new password of the administrator