# Linux Privilege Escalation Investigation

**Platform:** Blue Team Labs Online (BTLO)  
**Challenge:** Log Analysis – Privilege Escalation  
**Category:** Log Analysis / Linux Security  
**Difficulty:** Easy

## 1. Investigation Objective

Analyze a compromised Linux web server to understand how an attacker potentially escalated privileges from a restricted web server account to root-level access.

The scenario involved sensitive files being accessed despite the web server operating under the low-privileged `www-data` account.

## 2. Tools and Techniques

- Linux Bash history analysis
- Linux file permission inspection
- SUID privilege escalation concepts
- Python interpreter analysis
- Attacker command-line activity analysis

## 3. Investigation Process

### Initial Reconnaissance

Examined Bash history entries indicating attempts to identify the current user, inspect directories, and enumerate system information.

Commands such as `whoami`, `id`, and `ls -la` suggested that the attacker was investigating the environment and available permissions.

### Privilege Escalation Enumeration

Identified evidence of the attacker searching for root-owned files with the SUID permission bit enabled.

SUID allows a program to execute with the effective privileges of its file owner, potentially creating a privilege escalation risk when configured on an unsafe executable.

### Python-Based Privilege Escalation Attempt

Observed a Python command intended to launch a shell while preserving elevated privileges.

The sequence was consistent with an attempt to abuse an improperly configured SUID-enabled Python interpreter.

The available Bash history indicated the attempted technique but did not independently establish that privilege escalation succeeded.

### Additional Suspicious Activity

The command history also contained evidence of:

- Attempts to access sensitive system files.
- Inspection of sudo permissions and scheduled tasks.
- Use of network and process inspection utilities.
- An attempted download of Linux Exploit Suggester.
- Removal of a suspicious `.phtml` file from the web server's uploads directory.

The `.phtml` extension was particularly relevant because some web server configurations allow such files to execute PHP code, potentially bypassing upload restrictions that only block `.php`.

## 4. Key Findings

- The attacker performed extensive Linux system enumeration.
- The activity included searching for root-owned SUID executables.
- Python was used in a command consistent with an attempted privilege escalation.
- The Bash history contained indications of possible web shell activity.
- The evidence supported a potential SUID misconfiguration as the privilege escalation mechanism.

## 5. Security Recommendations

- Audit SUID-enabled executables and remove unnecessary elevated permissions.
- Restrict executable scripting files within web upload directories.
- Validate uploaded files using more than filename extensions.
- Monitor suspicious command execution and privilege escalation attempts.
- Apply least-privilege principles to web server service accounts.

## 6. Lessons Learned

This investigation improved my understanding of Linux privilege escalation, SUID permissions, attacker reconnaissance, and the importance of correlating command history with system configuration.

It also demonstrated that suspicious commands indicate attacker intent but do not always prove that an attack succeeded.
