# Overview
Today I performed Active Directory activities that most help desks do. This involves:
- Password resets and unlocks (happens mostly when a user forgot the password)
- Account Locked out after multiple attempts (happens when user typed the wrong password multiple times)
- Disable and enable account (this scenario depends on user status)
- Account and password expiration (this also depends on user status for accounts, security purposes for passwords)

## Password resets
Password resets can occur mostly when user forgets their own password. This can also happen whenever their current passwords
expire and needs to be reset in an set amount of time for security purposes. 

### What I did for this scenario:
First I lookup for the user's account name under Active Directory Users and Computers, in the Find Users, Contacts, and Groups option, this is also to verify if the said user
exists:             
<img width="890" height="597" alt="SearchUserAccount" src="https://github.com/user-attachments/assets/1b4bc53b-3f92-49c7-9754-0816c1708c20" />

After that, I right-clicked and reset the password of the account. I have to make a temporary password first for the user and make sure to
check the option "User must change password at next logon". What happens is that the temporary password is typed in first on the next logon before
the user could set their own password.
<img width="867" height="697" alt="ResetUserPassword" src="https://github.com/user-attachments/assets/711c7920-4c8e-4864-b128-4cd7f7cf5e32" /> <img width="785" height="582" alt="PasswordChanged" src="https://github.com/user-attachments/assets/3bae4325-5486-402c-a3f4-dd2d04714e65" />

The login prompt in the user's perspective:                
<img width="732" height="661" alt="PasswordChangePrompt" src="https://github.com/user-attachments/assets/8a425e38-b572-4be5-93ff-6288129f56c4" />

After the user's own password is entered:     
<img width="592" height="602" alt="PasswordChangedSuccess" src="https://github.com/user-attachments/assets/8008c49d-6fac-4684-b188-ff7aa63815f7" />

Once the reset, I double checked the password change by attempting to log in with the new password, I could confirm that the password is correct.
With that, the ticket about this scenario can be closed.


## Account locked out
The account gets locked out when the user attempted to use the wrong password multiple times. This is also a security feature that can be used
against brute force attacks.

### What I did for this scenario:
I checked the Properties of the account that is locked. Under the Account settings, I checked the checkbox "Unlock account". In the screenshot below, I already unlocked the account but when the account is locked, there will
also be an info that says the account currently locked in that checkbox:      
<img width="876" height="706" alt="UnlockAcc" src="https://github.com/user-attachments/assets/58c7834a-8240-40ec-956e-8fa48ad5c5ca" />

Afterwards, depending on the user, a password change may be needed in case they forgot. Otherwise, they can still use the same password to log in (in case that they remember their password 
or typed in the wrong key by mistake or they were using caps lock).
In this case, I logged in with the same password and can confirm that the account is now unlocked:          
<img width="720" height="756" alt="LogonSuccess" src="https://github.com/user-attachments/assets/b1db09e7-2aaa-4e8a-808b-19c1af958faa" />

### Problem that occured before this scenario:
I attempted to type the wrong password multiple times to get locked out. However, the lockout didn't happen because I have not 
set up an account lockout policy:          
<img width="821" height="607" alt="NoAccountLock" src="https://github.com/user-attachments/assets/914a465f-80d2-441a-895d-097d0e0375c5" />

To solve this, I opened the Server Manager, clicked Tools, and selected Group Policy Management. Under the Group Policy Management,
I navigated through Default Domain Policy -> Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies
-> Account Lockout Policy. Under the Account Lockout Policy, I set the attempts to 3 which will lock the account after 3 incorrect password attempts.                             
<img width="942" height="697" alt="AccLockoutSettings" src="https://github.com/user-attachments/assets/9cc678e7-3a1d-4a80-8a90-47622dbfeab2" />          
<img width="845" height="242" alt="AccLockEnabled" src="https://github.com/user-attachments/assets/c03d6446-0ae3-4bc6-957c-0c1bc401f69d" />

With that setting enabled, the account is now locked-out after more than 3 log-in attempts.       
<img width="717" height="612" alt="AccLocked" src="https://github.com/user-attachments/assets/0d9bba3d-a2ed-4fc7-a642-4048e7ae3bd1" />


## Disable and Enable Account
This scenario can happen whenever the user:
- has left the company
- is on an long leave
- account is requested by the HR to have it disabled for various reasons
                       
Overall, it depends on the status of the user on a corporate context.

### What I did for this scenario:
I went to the properties of the user's account -> Account options -> checked the box "Account is disabled" and clicked Apply:      
<img width="507" height="487" alt="AccDisableSetting" src="https://github.com/user-attachments/assets/2a80b8c8-e039-4881-bb01-c9ac221cb898" />

#### Here, the account is now disabled            
Active Directory perspective (Account name has an arrow icon):           
<img width="345" height="152" alt="AccountDisabled" src="https://github.com/user-attachments/assets/4c30e14a-e23d-4564-bdf5-bfe37ce56ecc" />

User perspective:      
<img width="701" height="595" alt="AccountDisabledUser" src="https://github.com/user-attachments/assets/7814747e-4114-424c-ba17-455ddbea764a" />

To enable the account again, simple uncheck same settings earlier and the user should now have an access again to their account.


## Account and password expiration
This scenario happens depending on context. For example:
- If the user is a temporary employee (or with a contract), the account made has an expiration date.
- If the user's password need to be updated every specified date (e.g. 6 months) for security purposes.

### For Account expiration:
Back in the user's account properties, I set the date for expiration and applied the settings:     
<img width="497" height="597" alt="SetExpDate" src="https://github.com/user-attachments/assets/d1f370c4-cc21-4862-8efe-72ca48a090fb" />

In the user's perspective:    
<img width="457" height="552" alt="AccountExpired" src="https://github.com/user-attachments/assets/d99e86aa-7ab3-475e-bd0b-57b77e47b9a1" />

### For password expiration: 
I went back to Default Domain Policy -> Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies
-> Password Policy and set the Maximum password age to 40 days, which means the user will be forced to change their password in the 40th day.
At the same time, the minimum password age is set to 30 days, meaning the users can now change their passwords in the 30th day.                   
<img width="886" height="692" alt="SetPassExpDate" src="https://github.com/user-attachments/assets/e022f288-2689-4708-8961-58beb727fc8e" />                  
<img width="932" height="377" alt="PassExpDateSetup" src="https://github.com/user-attachments/assets/2f369db4-a30f-4591-8b61-05519120d140" />

With the minimum password age is set, the user cannot change passwords within 30 days. That option restricted even if the user tries to do so.                                      
<img width="757" height="677" alt="ChangePassAttempt" src="https://github.com/user-attachments/assets/b498a516-03e6-48ce-b31c-a615aaa14936" />


Next, I will be learning about permission controls.




















