# cuckoo-autoinstall
The script "cuckoo.sh" will perform a full base install of the modified Cuckoo sandbox following the steps listed here: https://infosecspeakeasy.org/t/howto-build-a-cuckoo-sandbox/27

-Usage-
```
sudo ./cuckoo <cuckoo_path> <db_pass> <ip> <machinery>
```

If no arguments are provided, it will default to the following:

Cuckoo Path: /opt

DB Password: Pseudo-random generated by hashing date and then base64 encoding

Public IP: Attempts to discover public IP and use it during install

Machinery: kvm

Steps that need to take place after running script:

-Build sandbox VMs

-Modify configuration for new sandbox VMs

-Create user/pass for web portal
```
sudo htpasswd -c /etc/nginx/htpasswd $USER
sudo chown root:www-data /etc/nginx/htpasswd
sudo chmod u=rw,g=r,o= /etc/nginx/htpasswd
sudo service nginx restart
```

Tested on Ubuntu Server 16.04.1 LTS
