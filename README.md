# sqlinjection
Exploiting SQL Injection vulnerability

# AIM:
To exploit SQL Injection vulnerability using Multidae web application in Metasploitable2

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode


### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

SQL Injection is a sort of infusion assault that makes it conceivable to execute malicious SQL statements. These statements control a database server behind a web application. Assailants can utilize SQL Injection vulnerabilities to sidestep application safety efforts. They can circumvent authentication and authorization of a page or web application and recover the content of the whole SQL database. 
Identify IP address using ifconfig in Metasploitable2
## OUTPUT


<img width="720" height="400" alt="VirtualBox_Metasploitable2 ifconfig" src="https://github.com/user-attachments/assets/b8852c9f-b881-4b51-9ffc-ccdfb8d9ada2" />


Use the above ip address to access the apache webserver of Metasploitable2 from kali/parrot linux. In Kali Linux use the ip address in a web browser.
##  OUTPUT


<img width="958" height="898" alt="Screenshot 2026-05-21 134210" src="https://github.com/user-attachments/assets/71a7dcdf-6e04-4fef-bd6e-c49d36eb31e2" />


Select Multidae from the menu listed as shown above. The page is displayed as below:
##  OUTPUT


<img width="955" height="914" alt="Screenshot 2026-05-21 134225" src="https://github.com/user-attachments/assets/e1abae73-1176-4dad-935e-6c7e8d798dad" />


Click on the menu Login/Register and register for an account
##  OUTPUT


<img width="965" height="771" alt="Screenshot 2026-05-21 135616" src="https://github.com/user-attachments/assets/301f28b0-2e74-4cf8-9937-c18e56198b2b" />



Click on the link “Please register here”
##  OUTPUT

<img width="953" height="772" alt="Screenshot 2026-05-21 135710" src="https://github.com/user-attachments/assets/19483a50-3ba7-4c80-8b3f-682fb0eb1999" />


<img width="950" height="813" alt="Screenshot 2026-05-21 135730" src="https://github.com/user-attachments/assets/239a3b05-18c7-4c6f-b7fe-eb24f2a320af" />



Click on “Create Account” to display the following page:
##  OUTPUT


<img width="948" height="734" alt="Screenshot 2026-05-21 135826" src="https://github.com/user-attachments/assets/59996532-0bc2-4519-8b2c-2379289fef46" />



The login structure we will use in our examples is straightforward. It contains two input fields (username and password), which are both vulnerable. The back-end content creates a query to approve the username and secret key given by the client. Here is an outline of the page rationale:


($query = “SELECT * FROM users WHERE username=’$_POST[username]’ AND password=’$_POST[password]’“;).
 For the username put “ganesh” or “anything” and for the password put (anything’ or ‘1’=’1) or (admin’ or ‘1’=’1) then try to log in, and you’ll be presented with an admin login page.
##  OUTPUT

<img width="829" height="712" alt="Screenshot 2026-05-21 143638" src="https://github.com/user-attachments/assets/ee35e826-fd28-4187-a2ff-795000439bf4" />


Click “Login”. The logged in page will show as below:
##  OUTPUT

<img width="902" height="687" alt="Screenshot 2026-05-21 143705" src="https://github.com/user-attachments/assets/0656066a-0c5b-4d1a-8d42-0ba6f4621fd1" />



If error faced in registration follow the following steps in metasploitable 2:


<img width="814" height="684" alt="Screenshot 2026-05-21 143041" src="https://github.com/user-attachments/assets/b722449e-5ee7-49cf-8339-f728f59a8ca6" />



This issue is caused by a misconfiguration in the config.inc located in the /var/www/mutillidae folder on Metasploitable 2 VM.

Edit config.inc
Edit config.inc file located in /var/www/mutillidae folder on Metasploitable 2 by typing the following commands [one at the time]:
cd /
sudo nano /var/www/mutillidae/config.inc
Type msfadmin when prompted for the root password. 
Once nano opens config.inc file, look for the line $dbname = ‘metasploit’ as shown in Figure  below:
##  OUTPUT

<img width="919" height="707" alt="Screenshot 2026-05-21 143113" src="https://github.com/user-attachments/assets/cdf80638-8d03-4c00-859d-ec1e97e1ebb9" />


Replace ‘metasploit’ with ‘owasp10’ and make sure the lines end with semicolon ; as shown in Figure
##  OUTPUT


<img width="804" height="488" alt="Screenshot 2026-05-21 143259" src="https://github.com/user-attachments/assets/1b1aec10-e753-4d74-b81d-608b6783d409" />


Save and exit the config.inc
Save than exit the config.inc file by typing CTRL+X keys on your keyboard and the Y [Enter] when prompted to save the file
Restart the Apache server
To restart Apache, type the following command in the terminal. Alternatively, you can just reboot Metasploitalbe 2 VM.
sudo /etc/init.d/apache2 reload
##  OUTPUT

<img width="727" height="84" alt="Screenshot 2026-05-21 185950" src="https://github.com/user-attachments/assets/aca1a579-f144-46db-bd63-3ae925862272" />



# Reset Mutillidae database
Refresh the page then clicking on the Reset DB menu option to reset the Mutillidae database [Figure ]. Click OK when prompted.
##  OUTPUT


<img width="816" height="263" alt="Screenshot 2026-05-21 143515" src="https://github.com/user-attachments/assets/b692d91a-f502-49e4-a9fa-25b6a0b4129e" />



# Test the new configuration
Alright. Now is time to test if we managed to fix the database issue. Go ahead and register a new account on the Mutillidae webpage.

 The Mutillidae database error no longer appears 
## OUTPUT

<img width="805" height="309" alt="Screenshot 2026-05-21 143555" src="https://github.com/user-attachments/assets/2c57a736-8517-4230-96f1-2b174ade7b1a" />



Now after logging out you will see the login page. In the login page give ganesh’ # (myusername). You can see the page now enters into the administrator page as before when giving the password.
## OUTPUT


<img width="829" height="712" alt="Screenshot 2026-05-21 143638" src="https://github.com/user-attachments/assets/6af22069-1bd0-4986-8f25-e0e86807dbd1" />



Click the login button and you will see it enter into the administrator page.
## OUTPUT

<img width="902" height="687" alt="Screenshot 2026-05-21 143705" src="https://github.com/user-attachments/assets/dd27303c-3e5c-4360-97c3-35729c3ad261" />


## Union-based SQL injection

UNION-based SQL injection assaults enable the analyzer to extract data from the database effectively. Since the “UNION” operator must be utilized if the two inquiries have precisely the same structure, the attacker must craft a “SELECT” statement like the first inquiry. 
we will be using the “User Info” page from Mutillidae to perform a Union-Based SQL injection attack. Go to “OWASP Top 10/A1 — Injection/SQLi — Extract-Data/User Info” 

After logging out, Now choose the menu as shown below:
##  OUTPUT

<img width="964" height="805" alt="Screenshot 2026-05-21 171724" src="https://github.com/user-attachments/assets/3a215aa1-df9b-40f4-95d4-75859d343aa6" />



<img width="952" height="567" alt="Screenshot 2026-05-21 171846" src="https://github.com/user-attachments/assets/d273d7b1-ba16-4851-9ec9-f10f5e5c0c82" />



<img width="949" height="678" alt="Screenshot 2026-05-21 171820" src="https://github.com/user-attachments/assets/b95d3569-32fc-4677-a343-7c053e99b0c3" />



From this point, all our attack vectors will be performed in the URL section of the page using the Union-Based technique.There are two different ways to discover how many columns are selected by the original query. The first is to infuse an “ORDER BY” statement indicating a column number. Given the column number specified is higher than the number of columns in the “SELECT” statement, an error will be returned.
##  OUTPUT

<img width="791" height="636" alt="Screenshot 2026-05-21 172633" src="https://github.com/user-attachments/assets/f6475769-e1bd-4fa5-ab70-414c8e0edff5" />


Since we do not know the number of columns, we start at 1. To find the exact amount of columns, the number is incremented until an error related to the “ORDER BY” clause is returned. In this example, we incremented it to 6 and received an error message, so it means that the number of columns is lower than 6.

The browser url of this info page need to be modified with the url as below:
##  OUTPUT

<img width="944" height="174" alt="Screenshot 2026-05-21 180912" src="https://github.com/user-attachments/assets/f119e281-1535-41a6-b6cd-659d10a9f057" />



After adding the order by 6 into the existing url , the following error statement will be obtained:
##  OUTPUT

<img width="955" height="696" alt="Screenshot 2026-05-21 174732" src="https://github.com/user-attachments/assets/fa0743c2-3137-42e5-9ded-392fe7c65107" />



When we ordered by 5, it worked and displayed some information. It means there are five columns that we can work with. Following screenshot shows that the url modified to have statement added with ordered by 5 replacing 6.
## OUTPUT


<img width="958" height="266" alt="Screenshot 2026-05-21 180947" src="https://github.com/user-attachments/assets/b1d7a8ec-f079-410b-88ae-f0c9aa0e394f" />


 As it is having 5 columns the query worked fine and it provides the correct result
##  OUTPUT


<img width="959" height="972" alt="Screenshot 2026-05-21 174228" src="https://github.com/user-attachments/assets/ca197197-5a37-4ebc-bd81-56029a27190c" />


Instead of using the "order by" option, let’s use the "union select" option and provide all five columns. Ex: (union select 1,2,3,4,5).
##  OUTPUT

<img width="959" height="972" alt="Screenshot 2026-05-21 174228" src="https://github.com/user-attachments/assets/d494d1c8-f016-4e9f-9c00-0147185def6c" />


As given in the screenshot below columns 2,3,4 are usable in which we can substitute any sql commands to extract necessary information.
##  OUTPUT


<img width="957" height="686" alt="Screenshot 2026-05-21 181159" src="https://github.com/user-attachments/assets/eb7a01be-23cb-458e-be38-95a2d8ae5002" />




Now we will substitute some few commands like database(), user(), version() to obtain the information regarding the database name, username and version of the database.
##  OUTPUT


<img width="957" height="342" alt="Screenshot 2026-05-21 181451" src="https://github.com/user-attachments/assets/ce091df4-f628-4767-9382-323f6085d09a" />


The url when executed, we obtain the necessary information about the database name owasp10, username as root@localhost and version as 5.0.51a-3ubuntu5.
In MySQL, the table “information_schema.tables” contains all the metadata identified with table items. Below is listed the most useful information on this table.

Replace the query in the url with the following one:
union select 1,table_name,null,null,5 from information_schema.tables where table_schema = ‘owasp10’
##  OUTPUT


<img width="929" height="359" alt="Screenshot 2026-05-21 181659" src="https://github.com/user-attachments/assets/b54619bc-ec0f-4594-98dc-d7af1605b74c" />



The url once executed will  retrieve table names from the “owasp 10” database.
##Extracting sensitive data such as passwords 

When the attacker knows table names, he needs to discover what the column names are to extract data.

In MySQL, the table “information_schema.columns” gives data about columns in tables. One of the most useful columns to extract is called “column_name.”

Ex: (union select 1,colunm_name,null,null,5 from information_schema.columns where table_name = ‘accounts’).

Here we are trying to extract column names from the “accounts” table.
##  OUTPUT


<img width="955" height="796" alt="Screenshot 2026-05-21 183234" src="https://github.com/user-attachments/assets/47f19b4d-868a-40e8-8162-d8d029491d8b" />



The column names of the accounts is displayed below for the following url:


Once we discovered all available column names, we can extract information from them by just adding those column names in our query sentence.

Ex: (union select 1,username,password,is_admin,5 from accounts).
##  OUTPUT

<img width="952" height="859" alt="Screenshot 2026-05-21 184042" src="https://github.com/user-attachments/assets/2f165b72-b608-4606-812c-1b0ab8641eb6" />


## Reading and writing files on the web-server
We can use the “LOAD_FILE()” operator to peruse the contents of any file contained within the web-server. We will typically check for the “/etc/password” file to see if we get lucky and scoop usernames and passwords to possible use in brute force attacks later.

Ex: (union select null,load_file(‘/etc/passwd’),null,null,null).


##  OUTPUT


<img width="957" height="783" alt="Screenshot 2026-05-21 184333" src="https://github.com/user-attachments/assets/2afd9ac7-3b9c-45ad-9d82-40b226ad52b0" />



## RESULT:
The SQL Injection vulnerability is successfully exploited using the Multidae web application in Metasploitable2.
