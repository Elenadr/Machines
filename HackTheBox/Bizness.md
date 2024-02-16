Comenzamos realizando el escaneo de puertos con la ip facilitada, 10.10.11.252.

```bash
nmap -Pn -n -T4 --min-rate 4000 --max-rtt-timeout 2000ms -p- 10.10.11.252 --open
```


![](/Images/Pasted%20image%2020240209114916.png)

Mientras tanto lanzamos un mapeo específico a los puertos
```bash
nmap -Pn -n -T4 -sCV -p22,80,443,46115 10.10.11.252
```


![](../Images/Pasted%20image%2020240209122855.png)
Y un tercer escaneo con un script de vulnerabilidades:

```bash
nmap -Pn -n -T4 --script vuln -p22,80,443,46115 10.10.11.252
```
![](../Images/Pasted%20image%2020240209125406.png)
Si intentamos acceder a la url de la máquina en el navegador nos dará error, hay que editar el archivo /etc/host/ y añadir la siguiente línea:

![](/Images/Pasted%20image%2020240209121340.png)

Accedemos a la url:
https://bizness.htb/

![](../Images/Pasted%20image%2020240209121918.png)


Y escaneamos la url:
```bash
 dirb https://bizness.htb/
```
![](../Images/Pasted%20image%2020240209135126.png)
En el escaneo de dirb me encuentro subdominios interesantes, accedo al /contents que me redirige a:

> https://bizness.htb/content/control/main

![](../Images/Pasted%20image%2020240209123534.png)

Vamos a probar admin/admin
y pasa algo interesante
![](../Images/Pasted%20image%2020240209123805.png)Al rato el mensaje que nos manda es distinto
![](../Images/Pasted%20image%2020240209124459.png)Enciendo el burp e intercepto la petición
![](../Images/Pasted%20image%2020240209124636.png)

![](../Images/Pasted%20image%2020240209125231.png)
![](../Images/Pasted%20image%2020240209125231.png)

![](../Images/Pasted%20image%2020240209130647.png)

search

![](../Images/Pasted%20image%2020240209131512.png)
https://github.com/K3ysTr0K3R/CVE-2023-51467-EXPLOIT

![](../Images/Pasted%20image%2020240209133526.png)


![](../Images/Pasted%20image%2020240209134207.png)

![](../Images/Pasted%20image%2020240209134824.png)
![](../Images/Pasted%20image%2020240209141237.png)

![](../Images/Pasted%20image%2020240209141222.png)

![](../Images/Pasted%20image%2020240209141541.png)
```shell
hashcat -m 120 -a 0 -d 1 "b8fd3f41a541a435857a8f3e751cc3a91c174362:d" /usr/share/wordlists/rockyou.txt
```
![](../Images/Pasted%20image%2020240209143054.png)


![alt text](image.png)