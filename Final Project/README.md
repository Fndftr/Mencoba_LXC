Nama Kemlompok : 05

Anggota Kelompok:
1. Fendi Virgainsyah
2. Firman Arief

kelas: IF 01-02

------
# FINAL PROJECT SISTEM TERDISTRIBUSI REPORT
------
# Step by Step

------

Scheme :

![00_scheme](asset/setup.png)

------
1. Buat folder project
```bash
mkdir project
cd project
```

2.	buat LXC
```bash
lxc-create --name ubuntu20.1 --template download -- --dist "ubuntu" --release "focal" --arch amd64
lxc-create --name ubuntu20.2 --template download -- --dist "ubuntu" --release "focal" --arch amd64
lxc-create --name ubuntu20.3 --template download -- --dist "ubuntu" --release "focal" --arch amd64
lxc-create --name ubuntu20.4 --template download -- --dist "ubuntu" --release "focal" --arch amd64
lxc-create --name ubuntu20.5 --template download -- --dist "ubuntu" --release "focal" --arch amd64
lxc-create --name ubuntu20.6 --template download -- --dist "ubuntu" --release "focal" --arch amd64
lxc-create --name debian1 --template download -- --dist "debian" --release "buster" --arch amd64
lxc-create --name debian2 --template download -- --dist "debian" --release "buster" --arch amd64
lxc-create --name debianDB --template download -- --dist "debian" --release "buster" --arch amd64
```

![Alt text](./asset/continer.png)

3. cek ip WSL yang eth0 dan daftarkan ip wsl ke c:/Windows/System32/drivers/etc/hosts dengan domain kelompok05.fpsas

![Alt text](./asset/ifconfig.png)

![Alt text](./asset/hosts.png)

4. buat file ansible.cfg

```bash
nano ansible.cfg
```

![Alt text](./asset/01.jpg)

5. bikin file inventory

```bash
nano inventory
```

![Alt text](./asset/02.jpg)

6. bikin folder dan file untuk konfigurasi ansible laravel

```bash
mkdir -p roles/laravel/task
nano roles/laravel/task/main.yml
```

![Alt text](./asset/03.jpg)

7. bikin folder dan file untuk konfigurasi ansible wordpress 

```bash
mkdir -p roles/wordpress/task
nano roles/wordpress/task/main.yml
```

![Alt text](./asset/04.jpg)

8. bikin folder dan file untuk konfigurasi ansible yii 

```bash
mkdir -p roles/yii/task
nano roles/yii/task/main.yml
```

![Alt text](./asset/05.jpg)

9. bikin folder dan file untuk konfigurasi ansible codeigniter 

```bash
mkdir -p roles/codeigniter/task
nano roles/codeigniter/task/main.yml
```

![Alt text](./asset/06.jpg)

10. bikin folder dan file untuk konfigurasi ansible database

```bash
nano roles/db/task/main.yml
```

![Alt text](./asset/07.jpg)

11. edit konfigurasi 

```bash
nano /etc/nginx/sites-available/default
```

![Alt text](./asset/08.jpg)
![Alt text](./asset/09.jpg)

12. jalankan ansible untuk install laravel

```bash
ansible-playbook -i inventory roles/wordpress/tasks/main.yml -k
```

![Alt text](./asset/.jpg)

13. tampilan website laravel

![Alt text](./asset/10.jpg)


