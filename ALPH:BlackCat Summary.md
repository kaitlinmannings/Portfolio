## Executive Summary

ALPH/BlackCat is the first widely known ransomware written in Rust.
It requires an access token, which is a 32-byte value. It is executed by the
`-access-token` parameter. The encrypted configuration contains lists of
services and processes to stop whitelisted directories, files, file extensions,
and stolen credentials. The ransomware deletes all Volume Shadow Copies and
escalates privileges using the CMSTPLUA COM interface, and enables symbolic
links on the victim’s machine. The files are encrypted with AES, and the AES
key is encrypted with an RSA public key. The file extension is changed to
“uhwuvzu.”

## Tactics, Techniques, and Procedures

### Primary Tactic: Execution

ALPH/BlackCat executes by using a specified access token and utilizes various
Windows APIs and commande-line tools to perform its malicious activities,
including privilege escalation, file encryption and service/process termination.

#### Observables

| Observable Type   | Details                         |
|:------------------|:--------------------------------|
| file_hash | 847fb7609f53ed334d5affbb07256c21cb5e6f68b1cc14004f5502d714d2a456 |
| file_extension | .uhwuvzu |
| command_line | cmd.exe /c “vssadmin.exe Delete Shadows /all /quiet” |
|registry_entry | HKLM\SOFTWARE\Microsoft\Cryptography\MachineGuid |
| pipe | \.\pipe_rust_anonymous_pipe_.<Process ID>.<Random number> |

#### Techniques

T1486 Data Encrypted for Impact
T1059.003 Command and Scripting Interpreter: Windows Command Shell
T1543.003 Create or Modify System Process: Windows Service

#### References

- <https://securityscorecard.com/research/deep-dive-into-alphv-blackcat-ransomware/>
