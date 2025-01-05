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

## Step 10.

Next, I installed my Mythic C2 profile to Mythic and Apollo on to Mythic: 

![Home Lab24](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2023(Installing%20C2%20Profile%20for%20mythic).PNG) 

Installing Apollo:

![Home Lab25](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2024%20(Installing%20Apollo%20into%20mythic).PNG) 

The C2 profile and Apollo installed into Mythic:

![Home Lab26](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2025%20(Installed%20apollo%20agent%20and%20c2%20profile%20into%20mythic).PNG) 


## Step 11. 

Next, it was time to host my http module on my Mythic server so the malicious file could be downloaded onto my Windows client server. 

![Home Lab27](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2026%20(hosting%20http%20module%20using%20python3%20to%20download%20malicious%20file%20onto%20windows%20server).PNG) 

I then turned off real time protection on my Windows server as it would allow me to download the malicious file. 

![Home Lab28](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2027%20(turning%20off%20real%20time%20protection%20on%20windows%20server).PNG) 

Next it was time to invoke a web request to download the file. 

![Home Lab29](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2028%20(invoking%20webrequest%20to%20download%20malicious%20file).PNG)

As you can see, the file was then found in the downloads folder - I then ran the program. 

![Home Lab29](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2029%20-%20File%20then%20found%20in%20downloads%20windows%20server.PNG) 

Next, I went back to my Mythic and looked to see if the file had been downloaded or If I had an active callback, as you can see - it shows up. 

![Home Lab30](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2030%20File%20then%20shows%20as%20downloaded%20mythic.PNG)
![Home Lab31](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2031%20Active%20callback%20mythic.PNG)


## Step 12. 

Next it was time to download XAMPP onto my osTicket VM - This would allow me to host osTicket there. XAMPP was great to this as it would allow me to run a SQL server and well as an Apache server. In the steps below I will show how I did this and also 
how I set up PHPmyAdmin.

![Home Lab30](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2032%20Downloading%20Xampp.PNG)

Downloading osTicket. 

![Home Lab31](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2033%20Downloading%20osTicket.PNG)

Next I had to Change config file in XAAMP from the host ip to the IP of osTicket virtual machine. 

![Home Lab32](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2034%20Changing%20config%20file%20in%20XAAMP%20to%20IP%20of%20osTicket%20server-Apache%20domain%20name%20and%20SQL.PNG)

I then started both my apache and SQL server in XAMPP.

![Home Lab33](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2035%20PHP%20My%20admin.PNG) 

Next, it was time to change some settings in PhpmyAdmin on order to get osTicket to run correctly.

![Home Lab34](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2036%20PHP%20My%20admin%20set%20up.PNG)

![Home Lab35](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2037%20PHP%20My%20admin%20set%20up%20-Name%20in%20database.PNG)

In this next step I added the IP of my virtual machine to the host name.

![Home Lab36](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2038%20PHP%20My%20admin%20-%20Adding%20IP%20to%20host%20name.PNG)

I also had to change some settings in the config file for PHPmyAdmin - this was so I could access the dashboard again as the settings in the previous step would have not granted me access.

![Home Lab36](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2039%20PHP%20My%20admin%20-%20Changing%20config%20file%20to%20allow%20access.PNG)

I then had to edit privileges to my root account. I did this to be sure I would have all needed permissions to access the database.

![Home Lab37](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2040%20PHP%20my%20Admin%20-Editing%20privileges%20.PNG)

## Step 13.

In this step I started setting up my osTicket and linking it to my PhpmyAdmin databases. 

![Home Lab38](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2041%20Setting%20up%20osTicket.PNG)

![Home Lab39](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2042%20Finished%20setting%20up%20osTicket%20and%20finished%20linking%20to%20Php%20admin.PNG)

## Step 14. 

Before osTicket was fully setup, I needed to finish a few things.

The first thing was to edit a config file in osTicket. 

![Home Lab40](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2043%20Editing%20config%20file%20osTicket.PNG)

I also had to reset the config file using a command in powershell. 

![Home Lab41](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2044%20Editing%20config%20file%20osTicket%20-%20Powershell.PNG)

Then I was finished setting up osTicket! 


## Step 15. 

In this step, I needed to link osTicket using a webhook and an API key. 

![Home Lab42](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2045%20creating%20api%20key%20to%20link%20osticket%20to%20elastic.PNG) 

![Home Lab43](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2046%20(using%20a%20webhook%20to%20link%20osticket%20to%20elastic).PNG) 

As you can see below, our Webhook test failed - This was because we needed to add a firewall rule in our Windows osTicket VM which I will show below.

![Home Lab44](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2047%20(webhook%20test%20failed%20after%20using%20xml%20payload%20from%20ostickets%20github).PNG) 

Here is our new inbound firewall rule - to allow connections from port 80 and 443. 

![Home Lab45](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2048%20(new%20firewall%20rule%20for%20osticket%20VM).PNG) 

Next you can see how the Webhook test went. 

![Home Lab46](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2049%20(Test%20successful%20for%20webhook).PNG) 

## step 16. 

Now is was time to start generating telemetry using Metasploit in Kali Linux specifically - ssh brute force telemetry. 

I started Kali Linux and changed the directory to wordlists, I then navigated to a file called rockyou.txt. Next I unzipped the the file uzing gunzip. 

![Home Lab47](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2050%20(Using%20metaploit%20to%20generate%20brute%20force%20ssh%20telemetery).PNG)

Next I started the Metasploit console and then went to auxilliary/scanner/ssh/ssh_login and show options. The one I wanted to select was pass_file.

![Home Lab48](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2051%20Using%20metaploit%20to%20generate%20brute%20force%20ssh%20telemetery-Continued.PNG)

Next I selected the server I wanted to brute force which was my sshUbuntu server that I had enrolled as an agent under my fleet in Elastic and started the brute force. 

![Home Lab49](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2052%20(starting%20brute%20force).PNG)


## Step 17. 

In my last step of this lab setup, It was time to go back over to my Elastic agent and look for my ssh brute force activity. 

![Home Lab50](https://github.com/JWALL000/Home-Lab---Setup-/blob/main/Home%20LAB%20on%20premise%2053%20telemetry%20generated%20Brute%20Force%20SSH.PNG)

As you can see in that time frame I got alot of alerts pointing to authentication failure - so its safe to say we generated telemetry. 

































                                                                                      









































