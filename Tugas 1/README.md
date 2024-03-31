tugas virtualisasi web 

Nama : Fendi Virgainsyah

kelas: IF 01-02

NIM : 1203210086

1.	buat microservice 1
```bash
lxc-create --name microservice1 --template download -- --dist "ubuntu" --release "focal" --arch amd64
```
![Alt text](./asset/Picture1.png)

2.	buat microservice 2
```bash
lxc-create --name microservice2 --template download -- --dist "ubuntu" --release "focal" --arch amd64
```
![Alt text](./asset/Picture2.png)

3.	command # ip r -> untuk mengetahui ip dan subnet server dan microservice
```bash
ip r
```
![Alt text](./asset/Picture3.png)
```bash
lxc-ls -f
```
![Alt text](./asset/Picture4.png)

4.	masuk ke microservice1 dan microservice2 lalu install nginx dan network manager
```bash
lxc-attach -n microservice1
sudo apt install nginx nginx-extras
sudo apt install network-manager
```
![Alt text](./asset/Picture5.png)
```bash
exit
lxc-attach -n microservice2
sudo apt install nginx nginx-extras
sudo apt install network-manager 
```
![Alt text](./asset/Picture6.png)
```bash
exit
```

5.	setting static IP di microservice1
```bash
nano /etc/netplan/10-lxc.yaml
```
![Alt text](./asset/Picture7.png)
```bash
sudo netplan apply
ifconfig
```
![Alt text](./asset/Picture8.png)

6.	setting network interfaces
```bash
nano /etc/network/interfaces
```
![Alt text](./asset/Picture9.png)

7.	restart network manager
```bash
sudo systemctl restart NetworkManager
ifconfig
```
![Alt text](./asset/Picture10.png)

8.	Setting ngix
```bash
cd /etc/nginx/sites-available
touch microservice1.dev
nano microservice1.dev
```
![Alt text](./asset/Picture11.png)
```bash
cd ../sites-enabled 
ln -s /etc/nginx/sites-available/microservice1.dev . 
nginx -t 
nginx -s reload 
nano /etc/hosts
```
![Alt text](./asset/Picture12.png)
```bash
cd /var/www/html 
mkdir microservice1
cp index.nginx-debian.html microservice1/index.html 
cd microservice1
nano index.html
```
![Alt text](./asset/Picture13.png)

9.	Lakukan curl ke microservice1
```bash
curl -i http://microservice1.dev
```
![Alt text](./asset/Picture14.png)

10.	Setting Static IP microservice2
```bash
apt install nano net-tools curl 
sudo nano /etc/netplan/10-lxc.yaml 
```
![Alt text](./asset/Picture15.png)
```bash
sudo netplan apply 
ifconfig
```
![Alt text](./asset/Picture16.png)

Setting network interfaces
```bash
nano /etc/network/interfaces
```
![Alt text](./asset/Picture17.png)
```bash
sudo systemctl restart NetworkManager
ifconfig
```
![Alt text](./asset/Picture18.png)

Setting nginx
```bash
cd /etc/nginx/sites-available
touch microservice2.dev
nano microservice2.dev
```
![Alt text](./asset/Picture19.png)
```bash
cd ../sites-enabled
ln -s /etc/nginx/sites-available/microservice2.dev
nginx -t
nginx -s reload
nano /etc/hosts
```
![Alt text](./asset/Picture20.png)
```bash
cd /var/www/html 
mkdir microservice2 
cp index.nginx-debian.html microservice2/index.html 
cd microservice2
nano index.html
```
![Alt text](./asset/Picture21.png)
```bash
curl -i http://microservice2.dev
```
![Alt text](./asset/Picture22.png)

11.	Setting hosts di WSL 
```bash
nano /etc/hosts
```
![Alt text](./asset/Picture23.png)
```bash
cd /etc/nginx/sites-available
touch sister.local
nano sister.local
```
![Alt text](./asset/Picture24.png)
```bash
cd ../sites-enabled
sudo ln -s /etc/nginx/sites-available/sister.local .
sudo nginx -t
sudo nginx -s reload
```
![Alt text](./asset/Picture25.png)

Check apakah sudah ter-route dengan benar
```bash
curl -i http://sister.local
```
![Alt text](./asset/Picture26.png)
```bash
curl -i http://sister.local/blog
```
![Alt text](./asset/Picture27.png)
```bash
curl -i http://sister.local/aboutus
```
![Alt text](./asset/Picture28.png)
