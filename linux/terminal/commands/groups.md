# groups

To view the groups that a given user belongs to, run `groups USERNAME`.

```shell
# groups that john belongs to
groups john

# groups that current user belongs to
groups $whoami

# print out the groups of listed users
groups john sam zasy
```

If we just type `goroups` without arguments, by default it just lists current user's
groups
