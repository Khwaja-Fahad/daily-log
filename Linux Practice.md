# Linux Practice: Links, Permissions, Users and Text Processing

*Date: 2026-10-12 | Topic: Linux command line fundamentals*

This note covers what I practiced in a hands-on Linux session. The example names below are my own generic ones, written to explain the concepts.

---

## 1. Files, links and permissions

### Commands
```bash
mkdir project archive project/.shared          # create directories
touch project/report.txt project/.shared/notes.txt   # create empty files
ln project/report.txt project/.shared/report-copy    # hard link
ln -s ../project archive/shortcut                    # symbolic link
chmod 744 project/report.txt
chmod 2550 project/.shared
chmod 500 project archive
```

### Hard link vs symbolic link
| | Hard link | Symbolic link |
|---|---|---|
| Created with | `ln target name` | `ln -s target name` |
| Points to | the same data (same inode) | a path (like a shortcut) |
| If original is deleted | the data still exists | the link breaks |
| Check with | `ls -li` shows the same inode and link count 2 | `ls -l` shows `name -> target` |

### Things I learned
- A **relative symlink is resolved from the folder the link lives in**, not from where I ran the command. That is why the target is `../project` and not `project`.
- **Order matters.** I run `chmod` last. If I make a directory read-only first (`500`), I can no longer create anything inside it.
- Permission numbers: `r=4`, `w=2`, `x=1`. So `744` is `rwxr--r--`, and `500` is `r-x------`.
- A leading `2` is the **setgid** bit (`2550` is `r-xr-s---`). On a directory, new files inherit the directory's group.

---

## 2. Users, groups and special permissions

### Commands
```bash
getent group devs >/dev/null || sudo groupadd -g 900 devs
id alice >/dev/null 2>&1 || sudo useradd -m -u 2000 -g 900 -d /home/alice -s /bin/bash alice

sudo mkdir -p /var/data
sudo touch /var/data/report.htm
sudo chown alice:devs /var/data/report.htm
sudo chmod 0666 /var/data/report.htm
```

### Things I learned
- `groupadd -g` and `useradd -u -g -d -s` set exact IDs, home directory and shell.
- The `getent ... ||` and `id ... ||` checks make the script safe to run twice, because it only creates things that don't exist yet.
- **Run `chown` before `chmod`.** `chown` can clear the setuid/setgid bits, so setting permissions last keeps them.
- `mkdir -p` creates missing parent directories and doesn't complain if the folder exists.

### Special bits
| Number | Name | Meaning |
|---|---|---|
| `4xxx` | setuid | the file runs with its **owner's** privileges |
| `2xxx` | setgid | runs as the file's group, or on a directory, new files inherit the group |
| `1xxx` | sticky | on a directory, only the owner can delete their own files (like `/tmp`) |

### Why this matters for security
A setuid file owned by root is a classic **privilege escalation** target. Defenders audit for them with:
```bash
find / -perm -4000 -type f 2>/dev/null
```
Wrong permissions are one of the most common real-world misconfigurations, so knowing exactly what `rwx`, setuid and group ownership mean is core defensive knowledge.

---

## 3. Text processing: extracting data from HTML

### Task
Given several `.html` files with rows like `<tr><td>eth0</td><td>192.168.1.5/24</td></tr>`, print the interface names as one tab-separated line.

### Command
```bash
sed -n 's/^<tr><td>\([^<]*\)<\/td>.*/\1/p' files/*.html | paste -s -d '\t'
```

### How it works
- `files/*.html` selects every HTML file in the folder.
- `sed -n` prints only the lines I choose. `s/.../\1/p` keeps just the text of the first `<td>` (captured by `\( \)`).
- `[^<]*` means "any characters except `<`", which stops at the end of the cell.
- `paste -s -d '\t'` joins all lines into one, separated by tabs.

### Lesson
Regex works fine for a simple, predictable format like this, but it is fragile for real HTML. For real-world pages a proper parser is safer.

---

## Skills practiced
`mkdir` `touch` `ln` `ln -s` `chmod` `chown` `useradd` `groupadd` `getent` `sed` `paste` `find` `ls -li`
