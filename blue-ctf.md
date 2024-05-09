# Topic: Blue

# Subject:   CTF                                           

# Reported by : Shirinov Turan
### Note: IP address of machine may differ (I run the machine several time due to my mistake which mentioned) and I used THM.

nmap results:

![nmap(1)](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/6890f19b-9b1a-49a8-812d-28f2039af0c3)

![nmap2](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/4968dc46-08bd-4a1f-8987-b9a88f539dd1)

![nmap3](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/79e7950a-2853-46ba-8076-81b37bf7c134)

To be honest, machine name was Blue - so, I was expecting `eternal blue`.

Immediately searched the `Windows 7 Professional 7601 Service Pack 1` and we a have vulnerability also known as MS17-010.

I used Metasploit for this but upon several attempt - all of my trial failed!

The problem was - I did not set up my lhost properly (which I was using THM - I needed to set up as tun0)

So opon problem solved, let's do 2nd step:

I run `msfconsole` to start up the metasploit and searched for 'ms17-010' and set up the necessary `options`

And run:

![metasploitWIN](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/6bc666ce-c4ff-43f4-9aba-d67d50a60b31)

To open dos shell via the command 'shell' and run 'whoami'

![dos_shell](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/5ec578a8-3607-4866-8e1e-8ae00d4f85b7)

If we run `ps` - we will see the running process - we was needed to `migrate` the last process:

![migrating](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/dbea9b62-9c06-434e-b30d-5c91913074b9)

If we do CTRL+Z and back to meterpreter shell and see the users -  we have a user called 'Jon'. 
In meterpreter shell type `hashdump` to get the hashes and crack needed user.

![johntheripper](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/4dde87d9-9d8d-42ea-b0b1-1e4a56082bf5)

NOTE: Do not make my mistake which I did not copied the whole hash first which I was unable to crack it for that reason..

After that, we just needed to collect the flags:

The first flag was in C:

![flag1 txt](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/0d4aab02-4515-4bba-8c0d-620c4f1c16dd)

Second flag:

![flag2 txt](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/7e69a4e1-a721-472e-bc21-91ea9c68ca0a)
(location where passwords are stored within Windows) which I was running the `rundll32.exe keymgr.dll,KRShowKeyMgr` - it was wrong - we just needed to go \config

The next flag was in `Jon` Documents folder:

![flag3 txt](https://github.com/ShTuran/Practical-Ethical-Hacking/assets/111232034/9e2fbd5f-1897-49ca-a071-9023e3dad341)
