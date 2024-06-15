### user-management

**CRUD**
- Create 
    ```
        # create user
        sudo useradd <username>
        # set passwd and change passwd
        sudo passwd <username>
    ```
- Read 
    ```
        # to get user info about user
            whoami
            sudo cat /etc/passwd
            getent passwd <username>
            id username
    ```
- Update
    ```
        # update username
        sudo usermod -l <newusername> <oldusername>
        # To change home-folder, use
            sudo usermod -d /home/newHomeDir -m newUsername
    ```
- Delete
    ```
        sudo userdel <username>
    ```

**NOTE**:  Linux when you create user, a group with same name will be created

### group-management
**CRUD**

- Create 
    ```
        # create group
        sudo groupadd <name>
    ```
- Read 
    ```
        # to get user info about user
            sudo cat /etc/group
    ```
- Update
    ```
        # update username
        sudo groupmod -n <newname> <oldname>
    ```
- Delete
    ```
        sudo groupdel <username>
    ```
- operation
    ```
        # add user to group
        sudo usermod -aG groupname username

        # or
        sudo gpasswd -a username groupname
        
        # remove user from group
        sudo gpasswd -d username groupname
    ```