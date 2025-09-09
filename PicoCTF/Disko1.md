# Disko1 CTF – Writeup

## 📌 Challenge Description
The **Disko1** challenge focuses on disk forensics. The main objective is to analyze a provided disk image and uncover hidden information.  
This challenge tested basic Linux command usage, research on disk image structures, and forensic techniques such as searching for hidden strings.

---

## 🛠️ Steps & Solution

### 1. Extracting the File
The challenge file was compressed. I used the `gunzip` command to unzip it:


gunzip disko1.gz


This produced a raw disk image that could be investigated further.

---

### 2. Researching Disk Images
After extraction, I had a **disk image file**.  
Since I was new to this, I researched **what disk images are** and **how to analyze them**.

A disk image is a complete copy of the data and structure of a storage device. It often contains:
- File system structures  
- Hidden or deleted files  
- Metadata  

---

### 3. Analyzing the Disk
Based on my research, I explored different tools and commands to inspect the image:

- `file` → to identify the type of image  
- `fdisk -l` or `parted` → to view partition details  
- `mount` → to mount and browse the contents  
- Forensic tools like **sleuthkit** or **autopsy** → for deeper investigation  

---

### 4. Using `strings`
Since disk images may contain hidden messages or readable ASCII text within binary data, I used the `strings` command:


strings disko1.dd | pico


- This scans the binary file for **human-readable text**.  
- It is useful when searching for flags, passwords, or hidden clues.  
- In CTFs, flags are often left inside binary data, and `strings` makes them visible.  

Example (hypothetical output):
```
... random binary ...
CTF{hidden_text_inside_disk}
... random binary ...
```

---

## 🔑 Key Takeaways
- Learned how to use `gunzip` to extract compressed files.  
- Understood the role of disk images in digital forensics.  
- Practiced using system and forensic tools to explore disk structures.  
- Learned why `strings` is a simple yet powerful tool for uncovering hidden text in binary files.  

---


