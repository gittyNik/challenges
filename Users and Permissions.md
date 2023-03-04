Users & Permissions in Terminal (Ubuntu)
----------------------------------------

### Example

As a system administrator, you need to create a new user and grant them access to a specific folder.

To create a new user named `john`, you would run the following command:

```bash

`sudo adduser john`
```

This command will prompt you to set a password and additional information for the new user.

Next, you need to create a folder called `shared_folder` and grant `john` access to it. To create the folder, you can run the following command:

```bash

`sudo mkdir /var/shared_folder`
```
Now, you need to change the owner of the folder to `john`. To do this, run the following command:

```bash

`sudo chown john /var/shared_folder`
```
Finally, you need to grant `john` read and write permissions to the folder. To do this, run the following command:

```bash

`sudo chmod u+rw /var/shared_folder`
```
### Releases

#### Release 0: Create a new user

Create a new user named `bob`.

#### Release 1: Create a new folder

Create a new folder called `my_folder` in the home directory of `bob`.

#### Release 2: Change folder ownership

Change the ownership of `my_folder` to `bob`.

#### Release 3: Grant folder permissions

Grant `bob` read and write permissions to `my_folder`.

#### Release 4: Delete user and folder

Delete the user `bob` and the folder `my_folder`.

Note: Be careful when deleting users and folders, as this can cause data loss if not done correctly.

Good luck!












# Users & Permissions Challenge

In this challenge, you will learn how to manage users and permissions in Ubuntu terminal.

## Example

Create a new user named `testuser` with password `test123`.

```bash
sudo adduser testuser
sudo passwd testuser
```

Add `testuser` to the `sudo` group.

```bash
sudo usermod -aG sudo testuser
```

Verify that `testuser` has sudo privileges.

```bash
su testuser
sudo whoami
```

## Releases

### Release 0

Create a new user named `user1` with password `password123`.

### Release 1

Create a new group named `group1`.

### Release 2

Add `user1` to `group1`.

### Release 3

Create a new file named `file.txt` in the home directory of `user1`.

### Release 4

Change the ownership of `file.txt` to `user1` and the group ownership to `group1`.

Good luck!