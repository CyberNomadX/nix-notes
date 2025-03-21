# File & Directory Permissions

Linux permissions determine who can read, write, or execute files and directories. Here's a quick reference for working with permissions.

---

## 🔍 Viewing Permissions

Use `ls -l` to view file permissions:

```bash
ls -l
```

**Example output:**

```
-rwxr-xr-- 1 user group 4096 Mar 21  file.sh
```

---

## 🧵 Breakdown of Permission Strings

Each part of `-rwxr-xr--` has meaning:

```
[Type] [User] [Group] [Others]
   |       |       |      |
   |       |       |      └─── Permissions for everyone else
   |       |       └────────── Permissions for the group
   |       └────────────────── Permissions for the file owner (user)
   └────────────────────────── File type
```

---

### File Type Character (1st character)

| Character | Meaning            |
|-----------|---------------------|
| `-`       | Regular file        |
| `d`       | Directory           |
| `l`       | Symbolic link       |
| `b`       | Block device        |
| `c`       | Character device    |
| `s`       | Socket              |
| `p`       | Named pipe (FIFO)   |

---

### Permission Triplets (`rwx`, `r-x`, etc.)

Each triplet represents:

| Character | Permission | Meaning                              |
|-----------|------------|--------------------------------------|
| `r`       | read       | Can read the file or list directory  |
| `w`       | write      | Can write to the file or modify dir  |
| `x`       | execute    | Can run file or enter directory      |
| `-`       | none       | No permission                        |

So this:

```
-rwxr-xr--
```

Means:

- `-` → regular file  
- `rwx` → owner can read, write, and execute  
- `r-x` → group can read and execute (but not write)  
- `r--` → others can only read

---

## 🔧 `chmod` — Change Permissions

### Symbolic mode:

```bash
chmod u+x file.sh     # Give user execute permission
chmod g-w file.sh     # Remove write permission from group
chmod o+r file.sh     # Add read permission for others
chmod a+x script.sh   # Give everyone execute permission
```

### Numeric mode:

```bash
chmod 755 file.sh     # rwxr-xr-x
chmod 644 file.txt    # rw-r--r--
chmod 700 secret.sh   # rwx------
```

**Numeric breakdown:**

| Value | Permission |
|-------|------------|
| 7     | rwx        |
| 6     | rw-        |
| 5     | r-x        |
| 4     | r--        |
| 3     | -wx        |
| 2     | -w-        |
| 1     | --x        |
| 0     | ---        |

---

## 👑 `chown` — Change Owner

```bash
chown newuser file.txt          # Change owner to 'newuser'
chown newuser:newgroup file.txt # Change owner and group
```

Use `sudo` if you're not the file owner.

---

## 🧱 `chmod` on Directories

Permissions on directories:

- **r (read)** = list files in the directory
- **w (write)** = create or delete files
- **x (execute)** = enter the directory (`cd` into it)

So:

```bash
chmod 755 mydir     # Everyone can read/enter, only owner can write
chmod 700 secrets/  # Only owner can access
```

---

## 🧩 `umask` — Default Permissions

`umask` sets default permissions for new files and directories.

### Check your current umask:
```bash
umask
```

### Common defaults:
- `umask 022` → files: `644`, dirs: `755`
- `umask 077` → files: `600`, dirs: `700` (more secure)

---

## ✅ Quick Examples

```bash
chmod +x script.sh              # Make script executable
chmod 600 password.txt          # Only owner can read/write
chown root:root config.conf     # Give ownership to root
```

---

## Related

- [`navigation.md`](navigation.md) — moving around directories  
- [`search.md`](search.md) — finding files by name or permission

