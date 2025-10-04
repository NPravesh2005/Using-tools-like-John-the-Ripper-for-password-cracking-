# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
Cracked Passwords from Hash File

<img width="798" height="264" alt="Screenshot 2025-10-03 141922" src="https://github.com/user-attachments/assets/d53594c6-79e7-4fd9-8f94-8f99c95f9544" />

<img width="798" height="669" alt="Screenshot 2025-10-03 142222" src="https://github.com/user-attachments/assets/1f3a4101-3280-440c-b2ab-bef09dc3a48b" />

<img width="650" height="313" alt="Screenshot 2025-10-03 142332" src="https://github.com/user-attachments/assets/ace0dd25-7175-40d7-a0da-93ae430b6988" />

<img width="784" height="580" alt="Screenshot 2025-10-03 142359" src="https://github.com/user-attachments/assets/954db365-c275-4e13-9c30-e5eb055b82e1" />

<img width="807" height="247" alt="Screenshot 2025-10-03 142507" src="https://github.com/user-attachments/assets/c69f3b27-df04-402a-94cc-6cff646f12c4" />

<img width="599" height="77" alt="Screenshot 2025-10-03 142548" src="https://github.com/user-attachments/assets/0256c7ed-6352-4f93-afc3-74984f62eb85" />

<img width="649" height="530" alt="Screenshot 2025-10-03 142757" src="https://github.com/user-attachments/assets/b999c4f0-dfbc-4c91-a3f0-089019ab8215" />

<img width="803" height="420" alt="Screenshot 2025-10-03 143823" src="https://github.com/user-attachments/assets/88667b75-2e95-423b-a770-5144e3b52279" />

<img width="801" height="123" alt="Screenshot 2025-10-03 143912" src="https://github.com/user-attachments/assets/32f39954-1c21-46f0-86e0-e2effd430b0b" />

## RESULT:
The password hashes were successfully cracked using John the Ripper.

