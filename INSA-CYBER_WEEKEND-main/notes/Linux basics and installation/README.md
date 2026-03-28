🐧 Linux Basics & Installation Guide

📌 What is Linux?
Linux is an open-source operating system used in:

💻 Servers
🔐 Cybersecurity (like Kali Linux)
📱 Android devices
🧠 Development environments
👉 It is powerful, flexible, and widely used by hackers & engineers.

⚙️ Linux Basics
📁 File System Structure
/ → Root (main directory)
/home → User files
/root → Admin (root user)
/etc → Configuration files
/bin → Essential commands
/usr → User programs
/var → Logs & variable data
/tmp → Temporary files

💻 Basic Linux Commands
pwd        # show current directory
ls         # list files
cd         # change directory
mkdir      # create folder
rm         # delete file/folder
cp         # copy files
mv         # move/rename files

🔐 File Permissions
Controls who can read, write, or execute files
👥 Permission Types
u (user) → owner
g (group) → group users
o (others) → everyone else
🔑 Permission Symbols
r → read (view file)
w → write (edit file)
x → execute (run file)
-example:
-rwxr-xr--
Meaning:
user → rwx (read, write, execute)
group → r-x (read, execute)
others → r-- (read only)
🔢 Numeric (Octal) Values
r = 4
w = 2
x = 1
Example:
chmod 755 file.sh

⚙️ Commands
ls -l → show permissions
chmod → change permissions
chown → change owner
Example:

chmod 644 file.sh
chown user:group file.sh
-Common Permissions
755 → executable files
644 → normal files
700 → private files


🧰 Popular Linux Distros
🐉 Kali Linux → Cybersecurity
🟠 Ubuntu → Beginner-friendly
🎩 Fedora → Developers
🧊 Debian → Stable systems
💽 How to Install Linux (VirtualBox)
🖥️ Installation Steps
1️⃣ Download Tools

Install VirtualBox
Download Linux ISO (e.g., Kali Linux)
2️⃣ Create Virtual Machine
Open VirtualBox
Click New
Name: Kali Linux
RAM: 2GB+ (recommended 4GB)
3️⃣ Add ISO File
Select downloaded ISO
Start VM
4️⃣ Install OS
Choose Graphical Install
Follow setup steps
Create username & password
5️⃣ Login
Default for Kali (if prebuilt image):
username: kali
password: kali
🎯 Why Learn Linux?
🔐 Essential for cybersecurity
⚡ Full control over system
🧠 Used in servers & hacking tools
💼 High-demand skill

🔐 Security
Protects systems & data
CIA Triad:
-Confidentiality
-Integrity
-Availability

💻 Cybersecurity
Protects computers & networks from attacks
Common attacks:
-Phishing
-Malware
-DDoS
-MITM
