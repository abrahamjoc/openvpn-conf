# OpenVPN Administration
<p align=center>
   <img src=https://apprecs.org/gp/images/app-icons/300/af/net.openvpn.openvpn.jpg width=226 alt=logo>
</p>

## Blog Articles Reference 
[OpenVPN Configuration](https://www.digitalocean.com/community/tutorials/como-configurar-un-servidor-openvpn-en-ubuntu-16-04-es)


## Youtube Video Reference
[Server Configuration](https://www.youtube.com/watch?v=G6qkPLIkozE) \
[Client Configuration](https://www.youtube.com/watch?v=y8ed38eoUQw) \
[Duck DNS](https://www.youtube.com/watch?v=MLjKbake8HM)

## Server script configuration
```shell
sudo su
cd /etc/openvpn/easy-rsa
. ./vars
./build-ca
./build-key-server server
./build-dh
cp -a keys/* /etc/openvpn/
nano server.conf
openvpn --config /etc/openvpn/server.conf
```

## Create new user
```shell
sudo su
cd /etc/openvpn/easy-rsa
. ./vars
./build-key $VPN_USERNAME
./build-dh
cp -a keys/* /etc/openvpn/
systemctl restart openvpn@server
```

## Client configuration
Need this files for client.ovpn
* ca.crt (server file)
* $USERNAME.crt (client file)
* $USERNAME.key (client file)

Note: You must see client.ovpn format file and replace with your user data.