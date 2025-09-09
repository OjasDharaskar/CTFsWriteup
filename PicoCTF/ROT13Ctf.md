# MOD26 & 13 CTF – Writeup

## 📌 Challenge Description
Both **MOD26** and **13** challenges were cryptography-based tasks.  
The provided ciphertext looked like a scrambled text, but its pattern strongly resembled a common encoding scheme often used in beginner CTFs.  

The goal was to correctly decode the message to reveal the flag.

---

## 🛠️ Walkthrough / Solution

### 1. Observing the Ciphertext
The challenge gave a suspicious string that resembled CTF flag formatting (`CTF{...}`).  
The text pattern suggested a **simple substitution cipher**.  

---

### 2. Identifying ROT13
By analyzing the structure:
- The letters were shifted in a way that matched **ROT13** encryption.  
- ROT13 is a classic Caesar cipher with a shift of 13, and it is commonly used in CTFs as a simple obfuscation method.  

---

### 3. Using CyberChef
To decode it, I used **CyberChef**, a popular online tool for encoding/decoding.  

**Steps:**
1. Opened [CyberChef](https://gchq.github.io/CyberChef/).  
2. Added the **ROT13** recipe.  
3. Pasted the ciphertext.  
4. The output immediately revealed the correct flag.  

---

### 4. Why ROT13?
- The ciphertext closely resembled a flag format.  
- ROT13 is widely used in beginner challenges because applying it twice returns the original text (`ROT13(ROT13(x)) = x`).  
- It is simple, effective, and a common first guess in CTF crypto challenges.  

---

## 🔑 Key Takeaways
- Both **MOD26** and **13** challenges relied on simple Caesar shift logic.  
- **CyberChef** is a powerful and easy tool to test common encoding/decoding schemes.  
- Recognizing flag patterns (`CTF{...}`) helps in guessing the right cipher.  

---

## 🚀 Next Steps
- Experiment with other Caesar cipher shifts beyond 13 (ROT1–25).  
- Learn other common classical ciphers (Vigenère, Base32, Atbash, etc.).  
- Automate decoding with Python scripts (`codecs` or `cryptography` library).  

---

