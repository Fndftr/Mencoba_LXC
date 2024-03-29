# Mencoba_LXC
tugas virtualisasi web server
1.	lxc-create --name sister-local --template download -- --dist "ubuntu" --release "focal" --arch amd64 
![Alt text](./assets/picture1.png)
2.	lxc-create --name sister-local --template download -- --dist "ubuntu" --release "bionic" --arch amd64
![Alt text](./assets/picture2.png)
3.	command # ip r -> untuk mengetahui ip dan subnet server dan microservice
![Alt text](./assets/picture3.png)
# lxc-ls -f
![Alt text](./assets/picture4.png)
4.	masuk ke microservice1 dan microservice2 lalu install nginx dan network manager
# lxc-attach -n microservice1
# sudo apt install nginx nginx-extras
# sudo apt install network-manager
![Alt text](./assets/picture5.png)
# exit
# lxc-attach -n microservice2
# sudo apt install nginx nginx-extras
# sudo apt install network-manager 
![Alt text](./assets/picture6.png)
# exit
5.	setting static IP di microservice1
# nano /etc/netplan/10-lxc.yaml
![Alt text](./assets/picture7.png)
# sudo netplan apply
# ifconfig
![Alt text](./assets/picture8.png)
6.	setting network interfaces
# nano /etc/network/interfaces
![Alt text](./assets/picture9.png)
7.	restart network manager
# sudo systemctl restart NetworkManager
# ifconfig
![Alt text](./assets/picture10.png)
8.	Setting ngix
# cd /etc/nginx/sites-available
# touch microservice1.dev
# nano microservice1.dev
![Alt text](./assets/picture11.png)
# cd ../sites-enabled # ln -s /etc/nginx/sites-available/microservice1.dev . # nginx -t # nginx -s reload # nano /etc/hosts
![Alt text](./assets/picture12.png)
# cd /var/www/html # mkdir microservice1
# cp index.nginx-debian.html microservice1/index.html # cd microservice1
# nano index.html
![Alt text](./assets/picture13.png)
9.	Lakukan curl ke microservice1
# curl -i http://microservice1.dev
![Alt text](./assets/picture14.png)
10.	Setting Static IP microservice2
# apt install nano net-tools curl # sudo nano /etc/netplan/10-lxc.yaml  
# sudo netplan apply # ifconfig
![Alt text](./assets/picture15.png)
Setting network interfaces
# nano /etc/network/interfaces
![Alt text](./assets/picture16.png)
# sudo systemctl restart NetworkManager
# ifconfig
![Alt text](./assets/picture17.png)
Setting nginx
# cd /etc/nginx/sites-available
# touch microservice2.dev
# nano microservice2.dev
![Alt text](./assets/picture18.png)
# cd ../sites-enabled
# ln -s /etc/nginx/sites-available/microservice2.dev
# nginx -t
# nginx -s reload
# nano /etc/hosts
![Alt text](./assets/picture19.png)
# cd /var/www/html # mkdir microservice2 # cp index.nginx-debian.html microservice2/index.html # cd microservice2
# nano index.html
![Alt text](./assets/picture20.png)
# curl -i http://microservice2.dev
![Alt text](./assets/picture21.png)
11.	Setting hosts di WSL 
# nano /etc/hosts
![Alt text](./assets/picture22.png)
# cd /etc/nginx/sites-available
# touch sister.local
# nano sister.local
![Alt text](./assets/picture23.png)
# cd ../sites-enabled
# sudo ln -s /etc/nginx/sites-available/sister.local .
# sudo nginx -t
# sudo nginx -s reload
![Alt text](./assets/picture24.png)
Check apakah sudah ter-route dengan benar
# curl -i http://sister.local
![Alt text](./assets/picture25.png)
# curl -i http://sister.local/blog
![Alt text](./assets/picture26.png)
# curl -i http://sister.local/aboutus
![Alt text](./assets/picture27.png)
 
