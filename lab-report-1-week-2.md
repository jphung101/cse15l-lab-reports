> # **Installing VSCode**
---
1. Navigate to Visual Studio Code's website: https://code.visualstudio.com/
2. Download and launch VSCode, following all appropirate prompts and setting up all desired settings/preferences
3. When opened, **hit &nbsp;``Ctrl + ` ``**, this will **open** up the **Terminal** (which is where we will be running the commands to remotely connect)

---

> # **Remotely Connecting**
---
1. ### **Account Setup:**
- ***Note:*** If you already know your account credentials skip to **2. Remote Connection**
- **Navigate to https://sdacs.ucsd.edu/~icc/index.php**, and under "Account Lookup" enter your Username and Student ID
- Under **"Additional Accounts"**, click on the account's name button relevant to the course you are taking
    - **Ex:** *"cs15lwi22aql"*
![](Accounts.png)
    - "cse15l" being the course name
    - "wi" being the quarter you are taking the class
    - "22" being the year you are taking the class
    - "aql" being 3 unique characters for your account**
- Click on "change your password" and do so

2. ### **Remove Connection:**
- ***Note:*** If on **Windows**, navigate to: https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse to **install OpenSSH**
- In the **terminal**, **type &nbsp; `ssh [username]@ieng6.ucsd.edu`**
- Enter your password
    - ***Note:*** Even if you entered the **correct password**, you may **not be able to log in**. In this case **keep trying** and if the password prompt disappears, enter the above command again
- Results should look like this: ![](ssh.png)
- You are now connected!

---

> # **Trying Some Commands**
---

> # **Moving Files with `scp`**
---

> # **Setting an SSH Key**
---

> # **Optimizing Remote Running**
---
