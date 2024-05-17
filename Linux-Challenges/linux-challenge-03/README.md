# Linux Challenge-03

Since some new developers have joined our team, we need to perform following tasks for this challenge: 
- Create some users/groups
- Setup some permissions and access rights for them.

Architecture diagram:

<img src="./linux-challenge-03.png" alt="">

Run all the tasks with root user privilege. Do the following.

```bash
sudo su -
```

# Individual Steps

### Create Group Admins

<details>
<summary>Create a group called "admins".</summary>

```bash
groupadd admins
```
</details>

### Create User 'DAVID'

<details>
<summary>Create a user called "david" with shell "/bin/zsh and group admins</summary>

```bash
useradd david -g admins -s /bin/zsh 
```
</details>

<details>
<summary>Set "D3vUd3raaw" password for this user.</summary>

```bash
passwd david
```
Enter the given password and confirm it.
</details>

### Create User 'Natasha'

<details>
<summary>Create a user called "natasha" with shell "/bin/zsh" and group admins.</summary>

```bash
useradd natasha -g admins -s /bin/zsh
```
</details>

<details>
<summary>Set "DwfawUd113" password for this user.</summary>

```bash
passwd natasha
```

Enter the given password and confirm it.
</details>

### Create Group Devs

<details>
<summary>Create a group called "devs".</summary>

```bash
groupadd devs
```
</details>

### Create User 'RAY'

<details>
<summary>Create a user called "ray" with group devs and shell to "/bin/sh"</summary>

```bash
useradd ray -g devs -s /bin/sh 
```
</details>

<details>
<summary>Set "D3vU3r321" password for this user.</summary>

```bash
passwd ray
```

Enter the given password and confirm it.
</details>

### Create User 'LISA'

<details>
<summary>Create a user called "lisa" with group devs and shell to "/bin/sh".</summary>

```bash
useradd lisa -g devs -s /bin/sh
```
</details>

<details>
<summary>Set "D3vUd3r123" password for this user.</summary>

```bash
passwd lisa
```

Enter the given password and confirm it.
</details>

### File Ownership and Permissions

<details>
<summary>Make sure "/data" directory is owned by user "bob" and group "devs"</summary>

```bash
chown bob:devs /data
```
</details>

<details>
<summary>Also, make sure group "devs" and "user/group" owner has "full" permissions but "other" should not have any permissions.</summary>

```bash
chmod 770 /data
```
</details>

### Additional Permission via ACL

</details>

<details>
<summary>Give some additional permissions to "admins" group on "/data" directory so that any user who is the member the "admins" group has "full permissions" on this directory.</summary>

```bash
setfacl -m g:admins:rwx /data
```
</details>

### Sudoers

<details>
<summary>Make sure all users under "admins" group can run all commands with "sudo" and without entering any password.</summary>

```bash
vi /etc/sudoers
```

Enter the following line at the end of the file and save

```
%admins ALL=(ALL) NOPASSWD:ALL
```

</details>

### Sudoers

<details>
<summary>Make sure all users under "devs" group can only run the "dnf" command with "sudo" and without entering any password.</summary>

```bash
vi /etc/sudoers
```

Enter the following line at the end of the file and save

```
%devs ALL=(ALL) NOPASSWD:/usr/bin/dnf
```

</details>

### Set Resource Limit

<details>
<summary>Configure a "resource limit" for the "devs" group so that members of this group can not run more than "30 processes" in their session. This should be both a "hard limit" and a "soft limit", written in a single line.</summary>

```bash
vi /etc/security/limits.conf
```
Enter the following line at the end of the file and save

```
@devs            -       nproc           30
```
</details>

### Set Quota for Storage Space

<details>
<summary>Edit the disk quota for the group called "devs". Limit the amount of storage space it can use (not inodes). Set a "soft" limit of "100MB" and a "hard" limit of "500MB" on "/data" partition.</summary>

First, determine the device path for `/data`

```bash
mount | grep '/data'
```

Then set the quota on the device

```bash
setquota -g devs 100M 500M 0 0 /dev/vdb1
```
</details>
