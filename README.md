# Lockout-Ticket-Simulation
## Incident Response: Account Lockout (User Error Scenario)

During testing, I simulated a common real-world help desk issue where a user account becomes locked due to repeated incorrect password attempts.

---

### Ticket Summary
- **Issue:** User unable to log in due to account lockout  
- **User:** Carlos Borges  
- **System:** Domain-joined Windows 10 machine  
- **Severity:** Medium  
- **Category:** Account Lockout / User Error  

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/5984b094-220a-4538-a6ec-93dc40795526" />

---

### What Happened
The user attempted to log in multiple times with an incorrect password, which triggered the domain’s account lockout policy.

After **5 failed login attempts**, the account was automatically locked.

This generated:
- **Event ID 4625** → Failed login attempts  
- **Event ID 4740** → Account lockout  

<img width="1013" height="837" alt="image" src="https://github.com/user-attachments/assets/2112ea2b-c829-47f6-915d-06e9c7a6f4b9" />


---

### Investigation Steps

1. Checked login failures in Splunk:
2. Observed:
- Multiple failed attempts from the **same internal IP**  
- No unusual or external source activity  
<img width="579" height="492" alt="image" src="https://github.com/user-attachments/assets/62d12171-1b62-409e-95a6-db0c76177431" />


3. Verified lockout event:
- Event ID **4740** confirmed account was locked  
<img width="504" height="303" alt="image" src="https://github.com/user-attachments/assets/81400ec1-b454-489b-9b9b-19642e14e66e" />


4. Confirmed:
- Activity matched normal user behavior (not an attack)  
<img width="736" height="52" alt="image" src="https://github.com/user-attachments/assets/f18a0571-4a9e-43be-9761-f6364be2af6c" />

---

### Remediation Actions

- Unlocked the user account in Active Directory  
- Confirmed the user’s correct password  
- Advised the user to reset password if needed  
- Verified no suspicious activity was present  

<img width="787" height="535" alt="image" src="https://github.com/user-attachments/assets/5b725dfe-35b5-457f-8641-fc540493f33f" />

---

### What I Learned

- Not all account lockouts indicate malicious activity  
- How to differentiate:
- User error vs brute force attack  
- Importance of checking **source IP and behavior patterns**  
- How account lockout policies protect systems while still requiring support intervention  

---

### Outcome

- User regained access to their account  
- No security threat identified  
- Issue resolved as a standard help desk case  

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/ea9b64bd-fb70-4bf5-a621-d92504853513" />

---

### How This Connects to the Lab

This scenario demonstrates:
- Active Directory account management  
- Splunk log analysis for authentication events  
- Real-world troubleshooting of login issues  

It helped me understand how common authentication problems are handled in both IT support and security operations.
