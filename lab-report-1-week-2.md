> # **Installing VSCode**
---
1. Navigate to Visual Studio Code's website: [https://code.visualstudio.com/](https://code.visualstudio.com/)
2. Download and launch VSCode, following all appropirate prompts and setting up all desired settings/preferences
3. When opened, **hit &nbsp;``Ctrl + ` ``**, this will **open** up the **Terminal** (which is where we will be running the commands to remotely connect)
![](terminal.png)

---

> # **Remotely Connecting**
---
1. ### **Account Setup:**
    - ***Note:*** If you already know your account credentials skip to **2. Remote Connection**
    - **Navigate** to [https://sdacs.ucsd.edu/~icc/index.php](https://sdacs.ucsd.edu/~icc/index.php**), and under "Account Lookup" enter your Username and Student ID
    - Under **"Additional Accounts"**, click on the account's name button relevant to the course you are taking
        - **Ex:** *"cs15lwi22aql"*
    ![](Accounts.png)
        - "cse15l" being the course name
        - "wi" being the quarter you are taking the class
        - "22" being the year you are taking the class
        - "aql" being 3 unique characters for your account
    - Click on "change your password" and do so
2. ### **Remote Connection:**
    - ***Note:*** If on **Windows**, navigate to: [https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) to **install OpenSSH**
    - In the **terminal**, **type &nbsp; `ssh [username]@ieng6.ucsd.edu`**
    - Enter your password
        - ***Note:*** Even if you entered the **correct password**, you may **not be able to log in**. In this case **keep trying** and if the password prompt disappears, enter the above command again
    - Results should look like this: ![](ssh.png)
    - You are now connected!
    - To disconnect, **hit &nbsp; `Ctrl + D` &nbsp; or &nbsp;type &nbsp; `exit`**

---

> # **Trying Some Commands**
---
1. Now that you are connected, you can run commands on the server
2. Some include:
    - `pwd` (**P**rint **W**orking **D**irectory) to **print the directory** you are currently in
    - `ls` (**L**i**s**t) to **list the files, directories, and folders** in the current directory
    - `cd [directory/folder name]` (**C**hange **D**irectory) to **change** the **directory** you are currently working in
    - `cat [file name`] (Con**cat**enate) to **create a text file** and/or to **view the contents** of one
    - ***Note:*** you can type `man` (**Man**ual) in front of a command to **read more** about it and to see **more options** relevant to the command
![](lsa.png) 

---

> # **Moving Files with `scp`**
---
1. Be sure to disconnect before proceeding to avoid possible issues
2. Type `scp [filename] [username]@ieng6.ucsd.edu:~/` and login when prompted
3. ***Note:*** After the `scp` command is run, it logs you out
4. ***Optional:*** Type `ls` to see the file you copied over
![](scp1.png)

---

> # **Setting an SSH Key**
---
1. You may have noticed that I am able to connect to the server **without password prompts**, well, that's because of **SSH Keys**
2. On **your computer**, **type `ssh-keygen`**
3. When prompted to choose the destination file, simply hit `Enter`
4. Also hit `Enter` when prompted to enter a passphrase (to login without a password)
    - ***Note:*** If on **Windows**, follow [https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_keymanagement#user-key-generation) in addition
5. Copy the ***Public Key*** over to the `.ssh/authorized_keys` directory on the server
    - ***Public Key*** name is highlighted in the picture below: ![](keygen.png) 

> # **Optimizing Remote Running**
---
1. To run multiple commands in one line, you can simply add **`;` in between each command**![](commands.png)
2. To run commands right after ssh-ing to the server, you can type them at the end and include them in `"[commands]"` as if `" "` were **not included**, then the `ssh` command would run, the command right after it, **log you out**, and execute the rest of the commands on the client (your computer)


***Example:*** *Saving a Local Java File (and its edits) to a Server and Running It*
1. ### **Building the Command**
    - Begin with copying the file over with `scp [filename].java [username]@ieng6.ucsd.edu:~/`
    - Add a `;` at the end so another command can be run right after it:
        - `scp [filename].java [username]@ieng6.ucsd.edu:~/;`
    - As you are logged out, you must ssh again with `ssh [username]@ieng6.ucsd.edu`
    - To have your desired commands (compiling and executing the java file) run on the server, enclose them in `" "` right after the `ssh [username]@ieng6.ucsd.edu`. Also, seperate them with a `";"` so they can run one after another without interruption
        - `"javac [filename].java; java [filename]"`
        - `ssh [username]@ieng6.ucsd.edu "javac [filename].java; java [filename]"`
    - **In total, we now have:** 
    
    `scp [filename].java [username]@ieng6.ucsd.edu:~/; ssh [username]@ieng6.ucsd.edu "javac [filename].java; java [filename]"`
    ![](eff.png)
    - ***Note:*** This should take about **24 keystrokes to *set up***, assuming the above command is copied and all of the fill-ins are copied and pasted
        - Each copy and paste action is considered 4 keystrokes
2. ### **Running the Command**
    - Once run *at least **once***, you can simply hit the `Up Arrow` to pull the most recent command back again (which should be the command built in **1**) and hit &nbsp; `Enter`
    - ***Note:*** This should now take **2 keystrokes**


