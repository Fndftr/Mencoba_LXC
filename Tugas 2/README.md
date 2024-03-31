# Load Balancing dengan Round Robin

1.	Create microservice3
```bash
sudo lxc-create -n microservice3 -t download -- --dist "debian" --release "buster" –arch amd64
```
![Alt text](./assets/Picture1.png)
2.	Create microservice4
```bash
sudo lxc-create -n microservice4 -t download -- --dist "debian" --release "buster" –arch amd64
```
![Alt text](./assets/Picture2.png)
3.	Create microservice5
```bash
sudo lxc-create -n microservice5 -t download -- --dist "debian" --release "buster" –arch amd64
```
![Alt text](./assets/Picture3.png)
4.	Jalankan semua microservice yang telah di buat.
```bash
lxc-start -n microservice3
```
```bash
lxc-start -n microservice4
```
```bash
lxc-start -n microservice5
```
![Alt text](./assets/Picture4.png)

Konfigurasi microservice3
1.	Update dan Install nginx
```bash
lxc-attach microservice3
```
```bash
apt update
```
```bash
apt install nginx nano
```
![Alt text](./assets/Picture5.png)
```bash
nano /etc/hosts
```
![Alt text](./assets/Picture6.png)
#exitKonfigurasi microservice4
1.	Update dan Install nginx
```bash
apt update
```
```bash
apt install nginx nano
```
![Alt text](./assets/Picture7.png)
```bash
nano /etc/hosts
```
![Alt text](./assets/Picture8.png)
```bash
exit
```

Konfigurasi microservice5
2.	Update dan Install nginx
```bash
apt update
```
```bash
apt install nginx nano
```
![Alt text](./assets/Picture9.png)
```bash
nano /etc/hosts
```
![Alt text](./assets/Picture10.png)
```bash
exit
```
Konfigurasi Hosts wsl
```bash
nano /etc/hosts
```
![Alt text](./assets/Picture11.png)
```bash
sudo nano /etc/nginx/sites-available/sister.local
```
![Alt text](./assets/Picture12.png)
```bash
nginx -t	
```
```bash
nginx -s reload
```
![Alt text](./assets/Picture13.png)
```bash
curl -i app.sister.local
```
![Alt text](./assets/Picture14.png)
```bash
tail -f /var/log/nginx/app.sister.local-access.log
```
![Alt text](./assets/Picture15.png)