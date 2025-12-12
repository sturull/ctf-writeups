# Forensics Challenge 01 — Deleted File Recovery

## 📝 Challenge Description
A disk image was provided containing a deleted file.  
The goal was to recover the file and extract the hidden flag.

---

## 🔍 Step 1: Inspecting the Disk Image
I started by identifying the file system type:
file disk.img
Output showed an EXT4 filesystem.

Then I listed partitions:
fdisk -l disk.img
This revealed a single Linux partition.

---

## 💡 Step 2: Mounting the Image
I created a mount point:
sudo mkdir /mnt/ctf
sudo mount -o loop disk.img /mnt/ctf
Listing files:
ls -a /mnt/ctf
The deleted file was not visible, confirming it had been removed from the file system table.

---

## 🧪 Step 3: Recovering Deleted Files with `foremost`
I used **foremost** — a forensic tool for recovering deleted content:
sudo foremost -i disk.img -o recovered
This produced:
recovered/jpg/
recovered/png/
recovered/txt/
Inside the `txt` folder was a file named:
flag.txt
---

## 📂 Step 4: Extracting the Flag
I opened the file:
cat recovered/txt/flag.txt
Output:
FLAG{RECOVERED_SUCCESSFULLY}
Challenge completed.

---

## 📘 Lessons Learned
- EXT4 deleted files can often be recovered using carving tools  
- Mounting an image first helps determine structure and clues  
- `foremost` is a fast and effective recovery tool  
- Always preserve the original disk image before analysis  

---

## 🔐 Real-World Application
These skills apply to:

- Digital forensics investigations  
- Incident response  
- Data recovery  
- Malware analysis environments  
