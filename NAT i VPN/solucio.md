# NATVPN

## Configuració d'IPS

- IPFire: ![alt text](img/image.png)
- Zorin: ![alt text](img/image-1.png)
- Client: Està en DHCP. ![alt text](img/image-18.png)

## Serveis

Instal·lem els serveis apache2 i ssh si no els tenim instal·lats.

```bash
sudo apt install apache2
sudo apt install ssh
```

Editem la pàgina d'apache per possar el nostre nom.

```bash
sudo nano /var/www/html/index.html
```

![alt text](img/image-3.png)

Si introduim la nostra ip al buscador veurem com entrem a la web i es veu la pàgina.

![alt text](img/image-4.png)

## DNAT Regla SSH

Introduïm una nova regla. En aquest cas, utilitzem el port 2222.

![alt text](img/image-9.png)
![alt text](img/image-10.png)

### Comprovació SSH

Des d'un PC extern fem la seguent comanda:

```bash
ssh -p 2222 biel@10.0.2.17
```

![alt text](img/image-11.png)

## DNAT Regla HTTP

Entrem a IPFire i anem a cortafocs -> regles -> nova regla. Especifiquem d'orígen RED i activem NAT de destino. Com a destí, introduïm la IP del servidor (192.169.4.100)

![alt text](img/image-5.png)

Seleccionem:
- Protocol TCP
- Port 80
- Port extern NAT 80.

![alt text](img/image-6.png)

I ja tenim la regla creada.

![alt text](img/image-7.png)

### Comprovació HTTP

Comprovem que funciona amb la màquina client, introduïnt la IP RED.

![alt text](img/image-8.png)

## Configuració VPN

Per fer tots els certificats necessaris, anem a servicios -> openvpn -> generar certificados root/host.

![alt text](img/image-12.png)

Generem els certificats i ens mostrarà el de root, host i clau tls.

## Configuració VPN Certificats

Anem a tipus de connexió i deixem marcada la predeterminada. Després cliquem agregar.

![alt text](img/image-13.png)

A l'autenticació, introduim el nostre nom, país i contrasenya.

![alt text](img/image-14.png)

A les opcions avançades donem a Green i possem el DNS del servidor. 

![alt text](img/image-15.png)

Podem comprovar que ja s'ha creat.

![alt text](img/image-16.png)

Podem descargar el certificat.

![alt text](img/image-17.png)

## Configuració VPN Client (Windows)

Per editar l'arxiu de hosts de Windows, haurem d'anar a la seguent ruta:

```bash
C:\Windows\\System32\drivers\etc\hosts
```

Després, afegim una entrada amb el nostre domini. Ha de ser amb permisos d'administrador.

![alt text](img/image-19.png)

Instal·lem l'OpenVPN.

![alt text](img/image-20.png)

Fem servir scp amb el port 2222.

```bash
scp -P 2222 biel@10.0.2.17:/home/zorin/Downloads/biel.p12
"C:\Users\vboxuser\Downloads"
```

![alt text](img/image-21.png)

Quan entrem ens demana contrasenya del certificat que haurem especifitcat anteriorment.

![alt text](img/image-22.png)

Ara si anem a l'IPFire ja ens sortirà la connexió en CONECTADO.

![alt text](img/image-23.png)

## Comprovació de funcionament

Accedirem a la web amb l'IP privada. Farem ús de la VPN connectada. 

```bash
http://192.169.4.100
```

![alt text](img/Designer.png)

