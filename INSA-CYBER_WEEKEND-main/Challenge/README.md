# Week-2
##Day-1

File extraction 
challenge_1.txt

a. search for anything containing ¨FLAG¨ from the challenge_1.txt
bash : grep "FLAG" challenge_1.txt
-prints all lines containing ¨FLAG¨
-many lines could be fake or malformed

b. to extract the proper FLAG format
bash : grep -oE 'FLAG\{[A-Za-z0-9_]+\}' challenge_1.txt 
-o → show only the match, not the full line.
-E → enable extended regex.
'FLAG\{[A-Za-z0-9_]+\}' → matches FLAG{anything_inside}

c. remove duplicates
bash : grep -oE 'FLAG\{[^}]+\}' challenge_1.txt | sort | uniq
d. One-liner final command
-Clean, deduplicated, valid flags only
bash : grep -oE 'FLAG\{[A-Za-z0-9_]+\}' challenge_1.txt | sort -u
-this all lists all unique,correctly formatted flags.

e. to count how many flags found in the file 
bash : grep -oE 'FLAG\{[A-Za-z0-9_]+\}' challenge_1.txt | wc -l

f. to count all valid flags
bash : grep -oE 'FLAG\{[A-Za-z0-9_]+\}' challenge_1.txt | sort -u | head -n

![challenge](https://github.com/user-attachments/assets/b6956427-73c1-425d-86fe-21f1693da2a1)

challenge.jpn
1. to extract metadata(flag 1)
  bash :  exiftool challenge.jpn
Artist          : FLAG{ALWAYS_Check_Metadata}
Comment         : Some notes here
ImageDescription: Toy story wallpaper
2. to extract strings(flag2)
-filters out readable ASCII strings containing ¨FLAG¨
   bash :  strings challenge.jpn | grep -i ¨FLAG¨
expected outputg: FLAG{strings_leak_information}
3. to extract hidden files.
   binwalk -e challenge.jpg
result : flag4.txt

<img width="1278" height="772" alt="Screenshot From 2026-03-22 10-17-19" src="https://github.com/user-attachments/assets/9028e09c-e397-4a79-b3b7-a474ee01d18f" />

<img width="1278" height="682" alt="Screenshot From 2026-03-22 10-23-19" src="https://github.com/user-attachments/assets/59f78a9b-4f18-46d3-917a-98d1b754beb5" />

<img width="513" height="292" alt="Screenshot From 2026-03-22 14-11-04" src="https://github.com/user-attachments/assets/22e640d6-3241-4811-a943-ffd2dbd865a0" />
