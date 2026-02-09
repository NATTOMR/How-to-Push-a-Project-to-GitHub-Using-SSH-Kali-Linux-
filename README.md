
# 🔐 How to Push a Project to GitHub Using SSH (Kali Linux)

This guide explains how to securely push a project to GitHub using **SSH authentication** from a Kali Linux machine. SSH is more secure than HTTPS because it does not require passwords or tokens for every push.

---

## 📌 Prerequisites

* Kali Linux installed
* Git installed
* GitHub account
* Internet connection

---

## 🧰 Step 1 — Navigate to Project Folder

```bash
cd ~/Desktop/firewall\ project
```

---

## 🔧 Step 2 — Initialize Git Repository

```bash
git init
git add .
git commit -m "Initial commit"
```

---

## 🌿 Step 3 — Set Main Branch

```bash
git branch -M main
```

---

## 🔑 Step 4 — Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

When prompted for file name, press **Enter** to save in default location
(or provide custom name).

---

## 📄 Step 5 — View Public Key

If saved in default location:

```bash
cat ~/.ssh/id_ed25519.pub
```

If custom name used (example: natto):

```bash
cat natto.pub
```

Copy the entire key.

---

## 🌐 Step 6 — Add SSH Key to GitHub

1. Go to **GitHub Settings**
2. Open **SSH and GPG Keys**
3. Click **New SSH Key**
4. Paste your public key
5. Click **Add SSH Key**

---

## 🔗 Step 7 — Connect Local Repo to GitHub (SSH)

```bash
git remote set-url origin git@github.com:USERNAME/REPOSITORY.git
```

Verify:

```bash
git remote -v
```

---

## ▶️ Step 8 — Start SSH Agent & Add Key

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

(Use custom key path if different.)

---

## 🧪 Step 9 — Test SSH Connection

```bash
ssh -T git@github.com
```

Successful output:

```
Hi USERNAME! You've successfully authenticated...
```

---

## 🚀 Step 10 — Push Project to GitHub

```bash
git push -u origin main
```

Future pushes:

```bash
git add .
git commit -m "update"
git push
```

---

## 📂 Project Structure Example

```
firewall-project/
│── README.md
│── images/
│── firewall-types.png
│── stateless-firewall.png
```

---

## 🔐 Why Use SSH Instead of HTTPS?

| HTTPS                      | SSH                |
| -------------------------- | ------------------ |
| Requires token/password    | No password needed |
| Re-authentication required | One-time setup     |
| Less secure                | More secure        |

---

## ✅ Conclusion

Using SSH authentication in Kali Linux provides a secure and efficient way to push projects to GitHub. After initial setup, you can push updates without entering credentials each time.

---

## 👨‍💻 Author

**NATTOMR**
Cybersecurity & Networking Enthusiast

---
