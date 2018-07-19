# ansible-nginx
Instalasi nginx menggunakan ansible-playbook

## Pre-requirement
* Sudah membuat SSH RSA Key Pair untuk mesin dan target (supaya lebih efisien)
* Tutorial dapat dilihat [disini](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-ubuntu-1604)

## Implementasi
* Pull/ download repository ini
* Masuk ke direktori dengan terminal
* Edit file yang sudah terdownload, ubah pada bagian iptarget dengan menyesuaikan ip address dari mesin target
```
---
- hosts: iptarget
  become: yes
  tasks:
   - name: Nginx setup
     apt: pkg=nginx state=present update_cache=true
...
```
* Jalankan perintah berikut pada terminal:
```
ansible-playbook server-setup.yaml --become-method su --ask-become-pass
```
* Selanjutnya setelah command dieksekusi akan muncul prompt untuk memasukkan password super user dari mesin target, ketikkan dan tekan enter maka selanjutnya akan dilakukan proses instalasi nginx, tunggu sampai selesai
* Setelah selesai, anda dapat mengetesnya dengan mengakses ip address mesin target/ server melalui browser sehingga hasilnya adalah sebagai berikut:
![alt text](https://raw.githubusercontent.com/Zurin/ansible-nginx/master/ss_nginx.jpg)

