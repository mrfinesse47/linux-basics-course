# LINUX FILE PERMISSIONS

- Take me to the [Tutorial](https://kodekloud.com/topic/file-permissions-and-ownership/)

- In this lecture we will learn about various file type identifiers.
- We will also learn about various Linux file permissions that can be applied on the file or the directory.

  ![perm](../../images//perm.PNG)

  ![type](../../images//type.PNG)

#### Directory Permission

- To list the directory permission use

  ```
  [~]$ ls -ld /home/bob/random_dir
  ```

- To know the current user

  ```
  [~]$ whoami
  ```

- To change the change the directory

  ```
  [~]$ cd /home/bob/random_dir
  ```

#### File Permissions

- Linux file permissions are defined as

  ![filep](../../images//filep.PNG)

#### Modifying file permissions

- Use **`chmod`** command to modify the file permissions.

- Provide full access to owners

  ```
  [~]$ chmod u+rwx test-file
  ```

- Provide Read access to Owners, groups and others, Remove execute access

  ```
  [~]$ chmod ugo+r-x test-file
  ```

- Remove all access for others

  ```
  [~]$ chmod o-rwx test-file
  ```

- Full access for Owner, add read , remove execute for group and no access for others

  ```
  [~]$ chmod u+rwx,g+r-x,o-rwx test-file
  ```

- Provide full access to Owners, group and others

  ```
  [~]$ chmod 777 test-file
  ```

- Provide Read and execute access to Owners,groups and others

  ```
  [~]$ chmod 777 test-file
  ```

- Read and Write access for Owner and Group, No access for others.

  ```
  [~]$ chmod 660 test-file
  ```

- Full access for Owner, read and execute for group and no access for others.

  ```
  [~]$ chmod 750 test-file
  ```

In Unix-like operating systems, the execute (`x`) permission alone is not sufficient for executing scripts or programs because of how the system handles the execution process. Here's why execute-only permissions are not good enough:

1. **Read Permission for File Content**: When you execute a script or program, the operating system's kernel needs to read the file's content into memory to execute it. Even though you are not explicitly reading the file as a user, the system still requires read access to the file's content to load it into memory.

2. **Interpreter and Dynamic Libraries**: Many scripts and programs rely on interpreters or dynamic libraries to execute. The interpreter (e.g., `/bin/bash` for shell scripts) needs to read the script's content to interpret and execute its instructions. Dynamic libraries used by programs are also read from the filesystem.

3. **Security and Safety**: Read access is required for security reasons. It allows the system to check the script or program's integrity and confirm that it is not tampered with or corrupted. Without read access, the system would not be able to validate the file's contents before execution.

To maintain security and ensure the proper execution of scripts and programs, it's a best practice to grant both read (`r`) and execute (`x`) permissions when needed. This combination ensures that the system can load and execute the file securely while also protecting it from unauthorized modification.

In cases where you need to allow the execution of scripts without exposing their source code, you might consider using a more advanced solution like code obfuscation or packaging the script into a binary executable, but these are more complex and specialized approaches.

#### Change Ownership

- Changes owner to bob and group to developer

  ```
  [~]$ chown bob:developer test-file
  ```

- Changes just the owner of the file to bob. Group unchanged.

  ```
  [~]$ chown bob andoid.apk
  ```

- Change the group for the test-file to the group called android.

  ```
  [~]$ chgrp android test-file
  ```

  If you want to restrict a specific user ("user1") from reading a file, but another user in the "others" category has read access, you will need to use more advanced access control mechanisms like Access Control Lists (ACLs) or file ownership changes. Standard file permissions (`chmod`) alone cannot provide fine-grained access control for specific users within the "others" category.

Here's how you can achieve this using Access Control Lists (ACLs):

1. **Install ACL Tools (if not already installed):**

   Ensure that ACL tools are installed on your system. You can install them if necessary. On a Red Hat-based system like CentOS, you can use:

   ```bash
   sudo yum install acl
   ```

2. **Set Up an ACL for the User "user1":**

   Use the `setfacl` command to set up an ACL for "user1" on the file. Replace `/path/to/your/file` with the actual file path:

   ```bash
   sudo setfacl -m u:user1:- /path/to/your/file
   ```

   This command grants a negative ACL entry (`-`) for "user1," effectively denying read access.

3. **Verify the ACL:**

   To check the ACL for the file, you can use the `getfacl` command:

   ```bash
   getfacl /path/to/your/file
   ```

   The output should display the ACL, including the entry for "user1" with "deny" permission.

4. **Testing:**

   As "user1," try to access the file to confirm that access has been denied:

   ```bash
   su - user1
   cat /path/to/your/file
   ```

This approach allows you to grant or deny specific users access to a file while still allowing access to other users in the "others" category. Please note that ACLs provide more granular control but can be complex to manage, so use them judiciously and consider documenting your ACL configurations for future reference.

# HANDS-ON LABS

- Lets do some hands on labs to understand File Permission better. [Take me to Labs](https://kodekloud.com/courses/873064/lectures/17074516)
