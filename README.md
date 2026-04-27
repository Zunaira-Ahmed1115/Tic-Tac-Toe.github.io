# 🔐 Password Security System (8086 Assembly)

<p align="center">
  <img src="https://img.shields.io/badge/Language-8086%20Assembly-blue?style=for-the-badge">
  <img src="https://img.shields.io/badge/Platform-DOS%20CLI-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Tool-EMU8086-orange?style=for-the-badge">
  <img src="https://img.shields.io/badge/Status-Completed-success?style=for-the-badge">
</p>

---

## 👩‍💻 Author
**Zunaira Ahmed**  
*Computer Science Student | Assembly Language Enthusiast*

---

## 📌 Overview
The **Password Security System** is a low-level authentication program developed using **8086 Assembly Language**. It simulates a secure login system in a Command Line Interface (CLI) by verifying encrypted passwords and restricting unauthorized access.

---

## ✨ Key Features
- 🔑 Password authentication system  
- 🔒 Encrypted password storage (ASCII +1 method)  
- ⏳ Security delay after incorrect attempts  
- 🚫 System lock after 3 failed attempts  
- 🖥️ Lightweight CLI-based design  

---

## 🖼️ System Flow Diagram
```
        +----------------------+
        |   Start Program      |
        +----------+-----------+
                   |
                   v
        +----------------------+
        |  Enter Password      |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Encrypt User Input   |
        +----------+-----------+
                   |
                   v
        +----------------------+
        | Compare Password     |
        +----+-----------+-----+
             |           |
         Match        No Match
             |           |
             v           v
   +----------------+   +---------------------+
   | Access Granted |   | Decrease Attempts   |
   +----------------+   +----------+----------+
                                  |
                                  v
                      +------------------------+
                      | Attempts Left = 0 ?    |
                      +-----+------------+-----+
                            |            |
                           Yes          No
                            |            |
                            v            v
               +--------------------+   Retry
               |   System Locked    |
               +--------------------+
```

---

## 🔐 Encryption Logic
The system does not store the password in plain text.

➡️ Each character is shifted by **+1 ASCII value**

| Original | Encrypted |
|----------|----------|
| COAL123  | DPBM234  |

---

## ⚙️ How It Works
1. User enters password  
2. Input is encrypted in real-time  
3. Compared with stored encrypted password  
4. Access granted if matched  
5. Attempts reduced if incorrect  
6. System locks after 3 failures  

---

## 🛠️ Technologies Used
- **Language:** 8086 Assembly  
- **Environment:** DOS CLI  
- **Emulator:** EMU8086  
- **Concepts:**  
  - Interrupt Handling (`INT 21h`)  
  - String Manipulation  
  - Loops & Conditional Logic  

---

## 💻 How to Run (EMU8086)

1. Install **EMU8086 Emulator**  
2. Open the project `.asm` file  
3. Click **Compile & Run**  
4. Enter password in CLI  

---

## 🧪 Sample Output

### ✅ Correct Password
```
Enter Password: COAL123  
Access Granted - Level 1 User
```

### ❌ Wrong Password
```
Enter Password: abc  
Wrong Password! Security Delay Activated.
```

### 🔒 System Locked
```
SYSTEM LOCKED - CONTACT ADMIN
```

---

## ⚠️ Limitations
- Fixed password length  
- No password update feature  
- Single-user system  
- Basic encryption (not highly secure)  

---

## 🚀 Future Enhancements
- 🔐 Mask password input (`****`)  
- 👤 Add admin mode  
- 🔄 Enable password change  
- 🛡️ Implement stronger encryption  
- 👥 Multi-user authentication  

---

## 📈 Learning Outcomes
- Low-level programming concepts  
- Memory & register handling  
- Interrupt-based I/O  
- Secure input handling  
- Control flow in Assembly  

---

## 📌 Project Description
*A CLI-based password authentication system in 8086 Assembly with encrypted password verification, limited login attempts, and automatic system lock for enhanced security.*

---

## ⭐ Show Your Support
If you like this project, consider giving it a ⭐ on GitHub!