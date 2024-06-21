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