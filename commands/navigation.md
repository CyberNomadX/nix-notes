# Navigation Commands

These are essential Linux commands for moving around the filesystem, inspecting directories, and understanding where you are.

---

## `pwd` — Print Working Directory
Shows your current location in the filesystem.

```bash
pwd
```
**Example output:**
```
/home/kyle/scripts
```

---

## `cd` — Change Directory
Moves you to a different directory.

```bash
cd /path/to/directory
```

### Useful Variants:
```bash
cd ~        # Go to home directory
cd ..       # Go up one level
cd -        # Go to previous directory
```

---

## `ls` — List Directory Contents

```bash
ls          # List files and folders
ls -l       # Long format (permissions, ownership, etc.)
ls -a       # Show hidden files (those starting with .)
ls -lh      # Long format + human-readable file sizes
ls -la      # Long format + hidden files
```

---

## `tree` — Visualize Directory Structure

```bash
tree
tree -L 2   # Limit depth to 2 levels
```

> 📝 You may need to install it: `sudo apt install tree` or `sudo pacman -S tree`

---

## `find` — Search for Files by Name or Type

```bash
find . -name "*.sh"        # Find all .sh files in current dir and subdirs
find /etc -type f -name "hosts"
```

---

## `realpath` — Show the Absolute Path of a File/Folder

```bash
realpath ./script.sh
```

---

## `basename` / `dirname` — Strip Parts of a Path

```bash
basename /path/to/file.txt   # file.txt
dirname /path/to/file.txt    # /path/to
```

---

## Tips

- Use `Tab` to autocomplete folder names
- Combine with `&&` to run commands after navigating:
  ```bash
  cd /var/log && ls -lh
  ```

---

## Related

See also:  
- [`search.md`](search.md) for `find`, `locate`, and `grep`  
- [`permissions.md`](permissions.md) for file access commands

