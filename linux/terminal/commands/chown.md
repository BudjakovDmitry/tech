# chown

Command `chown` stands for "change ownership". It is used to change the owner and/or the
group owner of a specific file or directory.

Synopsis:

```shell
chown OWNER[:GROUP] FILE...
```

Example:

```shell
# make john the owner of file.txt
chown john file.txt
```

Only root user can change file's owner, so we must use `sudo` even current user is the
owner of the file.

To change the owner of a file and the file group owner at once we can provide both using
`chown USER:GROUP FILE`.

Example:

```shell
# change the owner of file.txt to john and
# change the file group owner to the group named students
chown john:students file.txt
```

To only change the group of a file, we can run `chown :GROUP FILE`.

```shell
# change the file group owner of file.txt to the group named students
chown :students file.txt
```

File's owner can change group owner, so if current user is the owner of the file we can
not to use `sudo`.
