## Project Overview 

In this project I successfully installed and configured multiple servers and operating systems to make a fully on premise home lab setup. This project allowed my to further develop my Cybersecurity IT skills and allowed me to gain a better understanding of
how a basic corporate network and security tools work together. 

I was inspired to do this project after seeing a video from Steven at the myDFIR Youtube channel who I owe a big thank you to for the knowledge and tips. 

In the below steps, I hope to show you how I achieved this and how much I have learned since starting the project. 

Thank you to whoever takes the time to have a look at this project - it is much appreciated! 

Lets begin. 


I ended up going with Virtual Box as a hypervisor as I was the most familiar with it, I also used 4 Ubuntu servers(ELK, Fleet, SHH, Mythic) 2 Windows servers (one as a target server, one for osTicket) and an instance of Kali Linux. 

![Home Lab](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%201.PNG) 

## Step.1 

I started by configuring and setting up my ELK server. I then also decided to do this via SSH on my host machine as I found it easier to manage. 

![Home Lab2](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%202(ELK%20configuration).PNG) 
![Home Lab3](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%203(ssh%20using%20powershell%20-%20to%20ELK%20server).PNG)
![Home Lab4](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%204(ssh%20using%20powershell%20-%20to%20ELK%20server%20-%20successx4).PNG)

## Step 2. 

I then installed Elasticsearch and Kibana onto my ELK server. 

![Home Lab5](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%205(downloading%20and%20installing%20elasticsearch%20and%20kibana).PNG)

## Step 3. 

Next, I created the encryption keys inside of Kibana. 

![Home Lab6](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%206(creating%20kibana%20encryption%20keys).PNG)


## Step 4. 

I then headed over to my Windows VM and installed Sysmon and the custom config.xml from Github, this would allow me to monitor system logs later on when needed. 

![Home Lab7](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%207(install%20sysmon%20on%20windows%20with%20the%20xml%20config%20file).PNG) 


## Step 5. 

I next went over to my web GUI for Elastic to then configure my fleet that would have my agents installed on them, It should be noted that in order for the web GUI to work, I had to set up a 
port forwarding rule inside of my hypervisor which I will show below.

![Home Lab8](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%208(fleet%20in%20elastic).PNG)
![Home Lab9](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%209(fleet%20in%20elastic%20-%20set%20up%20part%202%20).PNG) 
![Home Lab10](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2010(setting%20up%20fleet%20using%20ssh%20from%20host%20system%20).PNG)
![Home Lab11](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2011(elastic%20service%20running).PNG)
![Home Lab12](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20Lab%20on%20premise%2054%20-%20(Web%20GUI%20port%20forwarding%20rule).PNG)

## Step 6. 

Next, It was time to install the Elastic agent onto my Windows machine. 

![Home Lab13](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2012(elastic%20agent%20in%20windows).PNG)
![Home Lab14](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2013(setting%20upelastic%20agent%20in%20windows%20).PNG)
![Home Lab15](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2014(setting%20upelastic%20agent%20in%20windows%20-%20incoming%20data%20).PNG)
![Home Lab16](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2015(%20Dashboard%20overview%20).PNG)

## Step 7. 

I then installed the Elastic agent onto my Ubuntu server(SSH). 

![Home Lab17](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2016(%20Elastic%20Agent%20install%20on%20Ubuntu%20server%20).PNG)


## Step 8. 

Next it was time to install custom Windows logs into my fleet server using the web GUI. 

![Home Lab18](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2017(%20Adding%20custom%20windows%20logs%20integration%20into%20fleet%20).PNG)
![Home Lab19](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2018(%20Adding%20custom%20windows%20log%20integrations%20into%20Elastic%20Agent%20-%20Both%20Sysmon%20%26%20Defender%20%20).PNG) 


## Step 9. 

I then installed docker compose onto my Mythic server - this would be used to access to the containers needed to run my C2 server. I also added another port forwarding rule to access to the web GUI for Mythic. 

![Home Lab20](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2019%20(Installing%20docker%20compose%20into%20mythic%20server).PNG) 
![Home Lab21](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2020%20(Installing%20docker%20into%20mythic%20server).PNG)
![Home Lab22](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2021%20(After%20installing%20new%20port%20forwarding%20rule%20to%20virtual%20box%20for%20access%20to%20web%20GUI).PNG)
![Home Lab23](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2022%20(After%20getting%20access%20to%20web%20GUI).PNG)









































