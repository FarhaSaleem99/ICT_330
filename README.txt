 Install the GUI and Connect via RDP
Install GUI and RDP libraries:

1.sudo apt-get update
2.sudo apt-get upgrade
3.sudo DEBIAN=noninteractive apt-get -y install xfce4
4.sudo DEBIAN=noninteractive apt-get -y install xfce4-goodies
5.sudo apt install xfce4-session
6.sudo apt-get -y install xrdp 
7.sudo systemctl enable xrdp 
8.sudo adduser xrdp ssl-cert 
9.echo xfce4-session >~/.xsession
10.sudo systemctl restart xrdp

stop vm -> in network setting ->create port rule -> add inbound port-> in service type RDP->ADD-> START VM

To connect linux open remote desktop connection(Win+R, type mstsc) paste public ip->give sername and password
****************************************************

Hosting Webpage 
Stop the Vm → Go to network settings → create port rule → Inbound port rule → change 
service as “HTTP” → Add → overview →then start the vm →open putty again 
1.Sudo apt-get update 
2.Sudo apt-get install apache2
3.After installation, copy the public ip address of the VM and paste in browser→it will 
open apache server page
4.To create own website 
a. Go to root folder of apache server 
cd /var/www/html/
5.Check the file inside 
ls 
6. Edit the index.html file  
sudo nano index.html 
Or  
if we want, we can rename the file & edit 
sudo mv iindex.html demo.html 
sudo nano demo.html 
7. Delete the content already existing 
Ctrl + k → delete / backspace 
8.add our contentusing html tags
9.save and exit
ctrl+x
10.To see check the content 
Sudo cat demo.html 
Refresh the web page 
***************************************************************

docker
in VM
1.sudo apt-get update
2.sudo apt-get upgrade
3.  sudo apt install docker.io 
4. docker --version 
5.sudo docker images 
6.Pull the httpd and ubuntu images. 
o sudo docker pull httpd 
o sudo docker pull httpd: latest 
o sudo docker pull httpd: 2.4.57 
o sudo docker pull ubuntu 
o sudo docker pull ubuntu: lunar-20230816 
7.Run the httpd image on a container named “myhttpd” 
o sudo docker run -d -it --name myhttpd httpd 
8. Get docker image’s complete information. 
o sudo docker inspect [image_id] / [image_name] 
9.Check the history of the commits to a particular image. 
o sudo docker history [image_id] / [image_name] 
10. How to Save/Backup Docker Images. 
• You can save it as .tar format only. 
o sudo docker save [image_id / image_name] >sujah.tar 
• Use the ls command and check your backup file. 
11.List out the running containers 
sudo docker ps
12.To login container (myhttpd) [now container is the root]
sudo docker exec -it ubuntu-dev /bin/bash
ls
13.Create folder inside container
 mkdir folder1
14.Create Text file within that folder
cd folder1
touch readme.txt
ls
15.Install python 
apt-get install python3
apt-get update
apt-get install python3
16.select geaographical area
5
timezone
20
17.To check install or not
python3 --version
18.To save the changed in container type as exit
exit
sudo docker commit myhttpd release:1
19.Create a container that containing the released container
sudo docker run -d -it --name myhttpd-test-rel release:1
sudo docker ps
20.sudo docker exec -it myhttpd-test-rel /bin/bash
21.Docker repository
sudo docker push release:1
22.Login dockerHub
sudo docker login
sudo docker tag release:1 farhasaleem/release:1
sudo docker push farhasaleem/release:1
23.remove the image container using containerid
to get id 
sudo docker ps -a
sudo docker rm<containerid>
23.list out all containers and names
sudo docker ps -a

*********************
1.Create the Java Source File
nano hello.java or
create touch helllo.java->sudo nanohelllo.java
2.code for hello.java
public class hello {
    public static void main(String[] args) {
        System.out.println("Name: [Your Name]");
        System.out.println("Registration Number: [Your Registration Number]");
    }
}
3.save file 
ctrl+x and enter
4. Create a Docker Container in Interactive Mode
sudo docker run -it --name AppEnv -v $(pwd):/app openjdk bash
5.compile&run
cd /app
javac hello.java
java hello
6.to exit container
exit