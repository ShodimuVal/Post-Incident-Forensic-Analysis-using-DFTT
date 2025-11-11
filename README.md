# Applied Lab: Performing Post-Incident Forensic Analysis

## Description
This project was completed as part of my learning path toward the **CompTIA CySA+ certification**.  
The lab focused on post‑incident forensic analysis, including hidden partition discovery, deleted file recovery, and file carving from corrupted drive images.  
The exercises simulated real-world forensic investigations where evidence may be concealed, deleted, or intentionally destroyed.

---

## Objective
To acquire and analyze forensic evidence from compromised systems by:
- Inspecting forensic drive images for hidden partitions.
- Recovering deleted files from NTFS systems.
- Performing file carving on corrupted or damaged drive images.
- Applying forensic tools to validate findings and support incident response.

---

## Skills Learned
- Using forensic tools (`fdisk`, `testdisk`, `fiwalk`, `fsstat`, `mmls`, `fls`, `istat`) to analyze drive images.
- Mounting and inspecting forensic images in Linux.
- Identifying hidden partitions and extracting metadata.
- Recovering deleted files with `tsk_recover`.
- Performing file carving with `testdisk` to recover inaccessible files.
- Understanding the role of forensic analysis in the incident response lifecycle.

---

## Tools Used
- **Kali Linux VM** (analyst workstation)
- **Forensic images** from Digital Forensics Tool Testing (DFTT) repository
- **The Sleuth Kit (TSK)** utilities: `fdisk`, `fiwalk`, `fsstat`, `mmls`, `fls`, `istat`, `tsk_recover`
- **TestDisk** for partition analysis and file carving
- **Mount utilities** for accessing partitions

---

## Steps

### 1. Forensic Evaluation of a Drive Image
- Mounted `Student-Resources-L15.ISO` and extracted `ext-part-test-2.dd`.
- Used `fdisk` to display partition details; noted unaccounted sectors.
- Applied `testdisk` and `fiwalk` to reveal hidden partitions.
- Used `fsstat` and `mmls` to determine offsets.
- Extracted file information with `fls` and inode details with `istat`.
- Mounted hidden partition to `/mnt/p6` and confirmed presence of `second-3.txt`.

### 2. Recover Deleted Files
- Extracted `7-ntfs-undel.dd` from `7-undel-ntfs.zip`.
- Mounted image to `/mnt/temp7`; only `System Volume Information` visible.
- Ran `tsk_recover` to restore deleted files into `output` directory.
- Discovered recovered files including `frag1.dat`, `frag3.dat`, `mult2.dat`, `sing1.dat`.

### 3. File Carving
- Extracted `11-carve-fat.dd` from `11-carve-fat.zip`.
- Attempted to mount; failed due to corruption.
- Ran `fdisk` and `fiwalk`; errors indicated possible encryption.
- Used `testdisk` to perform file carving and recover files.
- Verified recovered images, including `haxor2.jpg`, `paul.jpg`, `pumpkin.jpg`, `shark.jpg`.
- Confirmed `pumpkin.jpg` contained cat images.

---

## Shared Responsibility & Risks
- **Analyst role:** Properly apply forensic tools to uncover hidden or deleted evidence.  
- **Risks:**  
  - Misinterpreting corrupted data as encryption.  
  - Overlooking hidden partitions or deleted files.  
  - Incomplete recovery due to overwritten sectors.  
- **Mitigations:**  
  - Use multiple forensic tools for cross‑validation.  
  - Document offsets, inode data, and recovered files.  
  - Share recovered evidence with the IRT for further investigation.

---

## Results
- **Hidden partition discovered:** Verified with `fdisk`, `testdisk`, and mounted successfully.  
- **Deleted files recovered:** `frag1.dat`, `frag3.dat`, `mult2.dat`, `sing1.dat` restored with `tsk_recover`.  
- **File carving successful:** Recovered corrupted image files, including `pumpkin.jpg` (cat image).  
- Reinforced CySA+ objectives:  
  - **1.1:** System and network architecture concepts in security operations.  
  - **1.2:** Indicators of malicious activity.  
  - **1.3:** Tools/techniques for malicious activity detection.  
  - **3.2:** Incident response activities.  
  - **3.3:** Post‑incident activity phases.  

This lab demonstrates practical forensic analysis techniques essential for incident response and evidence recovery — critical skills for the **CompTIA CySA+ certification journey**.
