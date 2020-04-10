# openVPN_ansible
##### RU

##### Запуск сервера

Тестировалось на VPS с ОС ubuntu 18.04 и Debian 9  
Перед запуском скопировать ip адрес сервера в hosts.yml

Для запуска сценария построения VPN сервера и цетра сертификации:  
`ansible-playbook create_ca_and_server.yml`

Для регистрации нового пользователя по имени:  
`ansible-playbook create_client.yml --extra-vars "client_name=<client_name>"`

Для отзыва сертификата пользователя по имени:  
`ansible-playbook revoke_client.yml --extra-vars "client_name=<client_name>"`

##### Запуск VPN на клиенте

После регистрации клиента по имени в папке `client_configs_from_remote` появится файл  
`<client_name>.ovpn`  
Файл передать клиенту. 

Пример запуска на клиенте под ubuntu:
`sudo openvpn --config <client_name>.ovpn`

Более подробно о способах запуска на разных платформах: 
https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-18-04

