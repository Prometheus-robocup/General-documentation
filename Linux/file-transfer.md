# SCP Command Guide for Linux Beginners

**Quick Command**: For sending from local to server (other computers)
```
scp -r -C /path/to/local/file user@ip.address:/path/to/receivers/folder
```
Use -C only if in a hurry.

## What is SCP?

SCP (Secure Copy Protocol) is a command-line utility that allows you to securely transfer files between computers on a network. It's based on the SSH protocol, ensuring your data is encrypted during transfer.

## When to Use SCP

Use the SCP command in these scenarios:

1. Copying files from your local computer to a remote server
2. Copying files from a remote server to your local computer
3. Copying files between two remote servers

## Basic SCP Syntax

The general syntax for SCP is:

```
scp [options] source destination
```

## Common SCP Commands

### 1. Copy a File from Local to Remote Server

```
scp /path/to/local/file username@remote_host:/path/to/remote/directory
```

Example:
```
scp Desktop/example.txt root@192.168.1.100:/home/remote_folder
```

### 2. Copy a File from Remote Server to Local

```
scp username@remote_host:/path/to/remote/file /path/to/local/directory
```

Example:
```
scp root@192.168.1.100:/home/remote_folder/example.txt ~/Desktop
```

### 3. Copy a File Between Two Remote Servers

```
scp username1@remote_host1:/path/to/file username2@remote_host2:/path/to/destination
```

Example:
```
scp root@192.168.1.100:/home/file.txt user@192.168.1.200:/home/destination
```

### 4. Copy Multiple Files

```
scp file1 file2 username@remote_host:/path/to/remote/directory
```

Example:
```
scp example1.txt example2.txt root@192.168.1.100:/home/remote_folder
```

### 5. Copy a Directory Recursively

Use the `-r` option to copy entire directories:

```
scp -r /path/to/local/directory username@remote_host:/path/to/remote/directory
```

Example:
```
scp -r Documents root@192.168.1.100:/home/backup
```

## Advanced SCP Options

- **Use a specific port**: `-P port_number`
  ```
  scp -P 2222 file.txt user@remote_host:/path/to/destination
  ```

- **Quiet mode** (suppress progress meter): `-q`
  ```
  scp -q file.txt user@remote_host:/path/to/destination
  ```

- **Verbose mode** (for debugging): `-v`
  ```
  scp -v file.txt user@remote_host:/path/to/destination
  ```

- **Limit bandwidth**: `-l limit_in_Kbit/s`
  ```
  scp -l 800 file.txt user@remote_host:/path/to/destination
  ```

- **Compress file during transfer**: `-C`
  ```
  scp -C file.txt user@remote_host:/path/to/destination
  ```

- **Preserve file attributes**: `-p`
  ```
  scp -p file.txt user@remote_host:/path/to/destination
  ```

## Tips for New Linux Users

1. Always double-check your syntax before executing an SCP command.
2. Use tab completion to avoid typos in file names and paths.
3. If you're unsure, use the `-v` (verbose) option to see detailed information about the transfer process.
4. Remember that SCP is case-sensitive, like most Linux commands.
5. Practice in a safe environment before transferring important files.