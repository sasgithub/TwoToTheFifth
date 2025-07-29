## depth – 2⁵ Submission, 2019

This is a 32-line Bash script submitted for Cerner's [2⁵ Programming Contest](https://github.com/cerner/2^5), 2019 edition.

### Overview

`depth` is a minimalistic tool to help users understand how deep they are nested in subshells. It recursively walks the process tree using `/proc` to count the levels between the current shell and a top-level ancestor like `systemd`, `init`, `sshd`, or a terminal process (`xterm`, `gnome-terminal`, etc.).

### Why Bash?

Bash is rarely used for recursive algorithms, making this an interesting challenge. This script demonstrates how recursion and process tree traversal can be performed even within the limitations of a shell script.

### Example Output

```bash
$ bash
$ ./depth
   ---bash---bash  (Depth=2)

# More complex example inside screen and sudo:
$ screen
$ sudo bash
# su - LabsAdmin
$ ./depth
   ---bash---bash---screen---screen---bash---sudo---bash---su---bash  (Depth=9)
```

### Requirements

  -  Linux system with a mounted /proc filesystem
  -  Bash 4.x or compatible shell
  -  The script must be executed in a subshell environment (e.g., nested bash, screen, etc.)

### Notes

  -  Screen may appear more than once – this is expected behavior due to how it spawns child processes.
  -  In some cases, similar output can be obtained using pstree, if the PID of the root shell is known.
  -  The recursion ends when the parent is one of: init, systemd, sshd, xterm, gnome-terminal.

### Limitations

    To comply with the 2⁵ (32-line) rule, the script avoids any error handling for missing or malformed /proc files.

    It assumes the /proc/[PID]/stat format remains consistent and readable.

    The depth count is approximate and relies on assumptions about session initiators.

    Bash recursion is not tail-optimized; this script is not suited for extremely deep trees.

Author: Scott Sesher 
