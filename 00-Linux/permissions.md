### File-Permission
files have different permissions or file modes, there three kinds of permissions .

- user
- group
- others

```
    ls -lrt
    drwxr-xr-x 2 pete penguins 4096 Dec 1 11:45 .
    filetype | user | group | others
    d        | rwx  | r-x   | r-x 
```
```
    d: directory
    r: readable
    w: writable
    x: executable (basically an executable program)
    -: empty
```
- modify permissions

    Changing permissions can easily be done with the `chmod` command.

    `u`-user,`g`-group,`o`-others

    `+` add | `-`remove

```    chmod u+r <filename>
    chmod ugo+r <filename>
    chmod ug+x <filename>
    chmod uo-w<filename>
```

There is another way to change permissions using numerical format. This method allows you to change permissions all at once. Instead of using r, w, or x to represent permissions, you'll use a numerical representation for a single permission set. So no need to specify the group with g or the user with u.

The numerical representations are seen below:

- 4: read permission
- 2: write permission
- 1: execute permission

    7=4+2+1
    
    6=4+2

    5=4+1

    752 = 7-user(rwx) | 5-group(rx) | 2-other(w)
    0=remove permission

``` chmod 421 <filename>
    chmod 700 <filename>
```

    
### owner-permission
- modify user ownership 
    ```
        chown <username> <filename>
    ```
- modify group ownership 
    ```
        chgrp <group> <filename>
    ```
- modify both user and group ownership 
    ```
        chown <username>:<groupname> <filename>
    ```






