# Mencoba_LXC
tugas virtualisasi web server
1.	lxc-create --name sister-local --template download -- --dist "ubuntu" --release "focal" --arch amd64 
![Alt text](./asset/picture1.png)
2.	lxc-create --name sister-local --template download -- --dist "ubuntu" --release "bionic" --arch amd64
![Alt text](./asset/picture2.png)
3.	command # ip r -> untuk mengetahui ip dan subnet server dan microservice
![Alt text](./asset/picture3.png)
# lxc-ls -f
![Alt text](./asset/picture4.png)
4.	masuk ke microservice1 dan microservice2 lalu install nginx dan network manager
# lxc-attach -n microservice1
# sudo apt install nginx nginx-extras
# sudo apt install network-manager
![Alt text](./asset/picture5.png)
# exit
# lxc-attach -n microservice2
# sudo apt install nginx nginx-extras
# sudo apt install network-manager 
![Alt text](./asset/picture6.png)
# exit
5.	setting static IP di microservice1
# nano /etc/netplan/10-lxc.yaml
![Alt text](./asset/picture7.png)
# sudo netplan apply
# ifconfig
![Alt text](./asset/picture8.png)
6.	setting network interfaces
# nano /etc/network/interfaces
![Alt text](./asset/picture9.png)
7.	restart network manager
# sudo systemctl restart NetworkManager
# ifconfig
![Alt text](./asset/picture10.png)
8.	Setting ngix
# cd /etc/nginx/sites-available
# touch microservice1.dev
# nano microservice1.dev
![Alt text](./asset/picture11.png)
# cd ../sites-enabled # ln -s /etc/nginx/sites-available/microservice1.dev . # nginx -t # nginx -s reload # nano /etc/hosts
![Alt text](./asset/picture12.png)
# cd /var/www/html # mkdir microservice1
# cp index.nginx-debian.html microservice1/index.html # cd microservice1
# nano index.html
![Alt text](./asset/picture13.png)
9.	Lakukan curl ke microservice1
# curl -i http://microservice1.dev
![Alt text](./asset/picture14.png)
10.	Setting Static IP microservice2
# apt install nano net-tools curl # sudo nano /etc/netplan/10-lxc.yaml  
# sudo netplan apply # ifconfig
![Alt text](./asset/picture15.png)
Setting network interfaces
# nano /etc/network/interfaces
![Alt text](./asset/picture16.png)
# sudo systemctl restart NetworkManager
# ifconfig
![Alt text](./asset/picture17.png)
Setting nginx
# cd /etc/nginx/sites-available
# touch microservice2.dev
# nano microservice2.dev
![Alt text](./asset/picture18.png)
# cd ../sites-enabled
# ln -s /etc/nginx/sites-available/microservice2.dev
# nginx -t
# nginx -s reload
# nano /etc/hosts
![Alt text](./asset/picture19.png)
# cd /var/www/html # mkdir microservice2 # cp index.nginx-debian.html microservice2/index.html # cd microservice2
# nano index.html
![Alt text](./asset/picture20.png)
# curl -i http://microservice2.dev
![Alt text](./asset/picture21.png)
11.	Setting hosts di WSL 
# nano /etc/hosts
![Alt text](./asset/picture22.png)
# cd /etc/nginx/sites-available
# touch sister.local
# nano sister.local
![Alt text](./asset/picture23.png)
# cd ../sites-enabled
# sudo ln -s /etc/nginx/sites-available/sister.local .
# sudo nginx -t
# sudo nginx -s reload
![Alt text](./asset/picture24.png)
Check apakah sudah ter-route dengan benar
# curl -i http://sister.local
![Alt text](./asset/picture25.png)
# curl -i http://sister.local/blog
![Alt text](./asset/picture26.png)
# curl -i http://sister.local/aboutus
![Alt text](./asset/picture27.png)
 
