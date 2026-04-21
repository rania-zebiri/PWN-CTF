# Pwn Exploitation Lab 🛡️

This repository contains a collection of Python exploit scripts developed using the `pwntools` library. These scripts were created as part of a learning journey focused on Binary Exploitation, following various **HackTheBox (HTB)** challenge walkthroughs and educational content on **YouTube**.

## 📚 Learning Context
These scripts demonstrate different techniques used to exploit memory corruption vulnerabilities. The primary learning resource used was the HackTheBox community on YouTube, which provides deep dives into:
* Stack Overflows & Return Oriented Programming (ROP)
* Format String Vulnerabilities
* Shellcode Injection
* GOT/PLT Redirection and Libc Leaking

---

## 📂 Script Catalog

### 1. Return Oriented Programming (ROP)
| File | Challenge | Technique |
| :--- | :--- | :--- |
| `auto_rop.py` | `ropme` | Automated ROP chain construction, Libc leak via `puts`, and spawning a shell. |
| `console_rop.py` | `htb-console` | Using a ROP chain to call `system` with a string injected via a "History of Fame" (HoF) feature. |
| `console.py` | `htb-console` | Manual ROP construction utilizing `pop rdi; ret` gadgets for x64 calling conventions. |

### 2. Format String Attacks
| File | Challenge | Technique |
| :--- | :--- | :--- |
| `fmtstr_auto.py` | `leet_test` | Uses `pwntools.fmtstr` to automate memory writes and bypass random number checks. |
| `format.py` | `format` | PIE and Libc base leaking via stack inspection, followed by a `__malloc_hook` overwrite. |
| `fuzz.py` | `nightmare` | A helper script to fuzz format string offsets to identify where user input sits on the stack. |
| `leet_test.py` | `leet_test` | Manual format string payload construction to overwrite `.data` section variables. |

### 3. Shellcode & Buffer Overflows
| File | Challenge | Technique |
| :--- | :--- | :--- |
| `batcomputer.py` | `batcomputer` | Stack address leak followed by shellcode injection and a jump to the stack. |
| `blacksmith.py` | `blacksmith` | Custom shellcode to `open`, `read`, and `write` a flag file directly to stdout. |
| `jeeves.py` | `jeeves` | Simple buffer overflow to overwrite a local variable on the stack to a specific value (`0x1337bab3`). |

---

## 🛠️ Key Utilities Included
Most scripts include a robust `start()` function that allows for seamless switching between different execution environments:
* **Local:** `python3 exploit.py`
* **GDB Debugging:** `python3 exploit.py GDB`
* **Remote Server:** `python3 exploit.py REMOTE <IP> <PORT>`

## ⚙️ Requirements
To run these exploits, you need the following installed:
* Python 3
* [Pwntools](https://github.com/Gallopsled/pwntools)
* GDB with [Pwndbg](https://github.com/pwndbg/pwndbg) (highly recommended for debugging)

---
*Note: These scripts are for educational purposes only and were developed to solve specific CTF challenges on the HackTheBox platform.*
