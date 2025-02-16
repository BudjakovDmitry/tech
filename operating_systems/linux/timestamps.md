# Timestamps

For each file system stores three different distinct timestamps.

## mtime

**Modification time**. It is when a file was last modified AKA when its content last
changed. If we rename file or change file permissions for example, the modification time
doesn't change.

When we type `ls -l` we see last modification time.

## ctime

**Change time**. Is when a file was last changed. This occurs anytime mtime changes but
also when we rename a file, move it, or alter permissions. So if *mtime* changes,
*ctime* changes as well.

We don't see this time by default, when we type `ls -l`. Type `ls -lc` to see this time.

## atime

**Access time**. Is updated when a file is read by an application or a command like
`cat`.
