Comenzamos realizando el escaneo de puertos con la ip facilitada, 10.10.11.252.

```bash
nmap -Pn -n -T4 --min-rate 4000 --max-rtt-timeout 2000ms -p- 10.10.11.252 --open
```


![](/Images/Pasted%20image%2020240209114916.png)

Si intentamos acceder a la url de la máquina en el navegador nos dará error, hay que editar el archivo /etc/host/ y añadir la siguiente línea:

![](/Images/Pasted%20image%2020240209121340.png)


Accedemos a la url:
https://bizness.htb/

![[../Images/Pasted image 20240209121918.png]]

