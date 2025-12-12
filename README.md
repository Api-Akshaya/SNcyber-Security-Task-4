Password Cracking Using John the Ripper (MD5crypt)

This project demonstrates a controlled password-cracking exercise using John the Ripper.  
The objective is to understand how dictionary attacks operate and why weak passwords are insecure.

1. Overview

In this exercise, we used John the Ripper to crack an MD5crypt hash.  
The process illustrates:

- How password hashes are stored.
- How dictionary attacks are performed.
- The risks associated with weak or common passwords.
- The importance of secure password practices.

2. Files Used

2.1 hash.txt  
Contains the MD5crypt hash:

$1$hackme$dT0ZqgGbCqVA1cCszn8Kf/

2.2 pwlist.txt  
A custom wordlist created for testing:

password123

3. Tools Required

- Kali Linux  
- John the Ripper  
- Terminal access  

4. Procedure

Step 1: Create the hash file
echo "$1$hackme$dT0ZqgGbCqVA1cCszn8Kf/" > hash.txt

Step 2: Create the custom wordlist
printf 'password123\n' > pwlist.txt

Step 3: Ensure no previous John sessions are running
pkill -f john || true

Step 4: Execute John the Ripper
john --format=md5crypt --wordlist=pwlist.txt hash.txt

Cracking Result  
John successfully identified the password during execution:

password123

yaml
Copy code

This confirms that the plaintext password for the given hash is **password123**.

5. Explanation of the Attack

John the Ripper performs a dictionary attack by:

1. Reading each entry from the wordlist.
2. Hashing it using the MD5crypt algorithm.
3. Comparing it with the target hash.
4. Reporting a match when found.

Since "password123" is a common and weak password, it was cracked instantly.

6. Security Analysis

This activity demonstrates that:

- Weak passwords can be cracked quickly using basic tools.
- Hashing alone is not sufficient; strong password selection is critical.
- Modern systems should use advanced hashing algorithms such as bcrypt, PBKDF2, or Argon2.
- Organizations must enforce strong password policies.

7. Conclusion

The MD5crypt hash was successfully cracked using John the Ripper and a simple dictionary attack.  
This practical exercise reinforces the importance of choosing strong, unique passwords and adopting secure cryptographic practices in real-world systems.



