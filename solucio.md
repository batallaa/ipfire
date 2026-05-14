# IPFire

## Màquina virtual

Especificacions de la màquina:

![alt text](img/image.png)

## Instal·lació IPFire

Entrem a l'IPFIRE i ens preguntarà si volem instal·lar-lo. Pressionem la primera opció.

![Captura 1](img/image-1.png)

Seleccionem el nostre idioma preferible. En el meu cas Espanyol.

![alt text](img/image-2.png)

Continuem.

![alt text](img/image-3.png)

Seleccionem borrar totes les dades.

![alt text](img/image-4.png)

Seleccionem el sistema d'arxius ext4.

![alt text](img/image-5.png)

Reiniciem el sistema.

![alt text](img/image-6.png)

Seleccionem el tipus de teclat.

![alt text](img/image-7.png)

Seleccionem la nostra zona horària.

![alt text](img/image-8.png)

Introduim de nom "ipfire".

![alt text](img/image-9.png)

Posem el nom del domini.

![alt text](img/image-10.png)

Introduïm la contrasenya d'admin.

![alt text](img/image-14.png)

Després introduïm contrasenya de root.

![alt text](img/image-11.png)

Seleccionem configuració de xarxa "GREEN + RED".

![alt text](img/image-15.png)

Assignem tarjetes per a les dos xarxes.

![alt text](img/image-16.png)
![alt text](img/image-17.png)

Ara configurem les dos interfícies.

Per la GREEN utilitzarem la seguent ip: 192.169.x(4).254

![alt text](img/image-18.png)

Amb la RED utilitzarem DHCP.

![alt text](img/image-19.png)

Introduïm l'IP i tota la informació i proseguim.

![alt text](img/image-20.png)

Ara podem iniciar sessió i veiem com podem entrar.

![alt text](img/image-21.png)

## Configuració del client

Modifiquem l'IP a la màquina client.

![alt text](img/image-23.png)

Entrem a IPFire des de l'URL: 

```bash
https://192.169.4.254:444
```

![alt text](img/image-22.png)

## Configuració bàsica

Per activar el proxy en green dins de l'IPFire, anem a Red -> Web Proxy, activem la casella d'activat en green.

![alt text](img/image-24.png)

Configurem les IPs del Proxy amb els ports corresponents.

![alt text](img/image-25.png)

## Activitats

### Llistes negres

Per personalitzar la llista negra, anem a Red -> Filtre URL. Baixem abaix i modificarem la URL d'orígen personalitzada.

![alt text](img/image-26.png)

Després, entrarem a la URL i baixarem l'arxiu. Després, l'adjuntem.

![alt text](img/image-27.png)

Després adjuntem l'arxiu i el pugem.

![alt text](img/image-29.png)
![alt text](img/image-28.png)

### Bloquejar pàgines

Bloquejem les pàgines de radio i banc dels filtres.

![alt text](img/image-30.png)

Abaix, bloquejem les URLs de les dos pàgines: ingdirect.es i ah.fm

![alt text](img/image-34.png)

Després, comprovem si es bloquejen les pàgines.

![alt text](img/image-31.png)
![alt text](img/image-33.png)

### Bloqueig de dominis

Possem els dos dominis que ens demanen a la caixa de llista negra.

![alt text](img/image-35.png)

Després comprovem si estàn bloquejades.

![alt text](img/image-36.png)
![alt text](img/image-37.png)

### Bloqueig d'URL concreta

Per aquest apartat, faré ús  de l'URL:

```bash
neverssl.com/online
```

Anem a Blacklists i introduïm la url que volguem bloquejar.

![alt text](img/image-38.png)

I si provem un cop fet aquest canvi a entrar a la web, no ens deixarà.

![alt text](img/image-39.png)

Però si entrem a un altre domini de la pàgina, ens deixarà accedir.

![alt text](img/image-40.png)

### Bloqueig anime excepte un domini

Per bloquejar totes les pàgines relacionades amb anime, anem a filtratge d'url i introduïrem la paraula "anime" dins el requadre "llista de frases personalitzades".

![alt text](img/image-42.png)

Després per deixar que un sol domini relacionat amb l'anime es pugui accedir, possarem l'url del domini a la whitelist.

```bash
animenewsnetwork.com
```

![alt text](img/image-43.png)

Si intentem entrar a una pàgina d'anime qualsevol veurem que no ens deixa. En el meu cas ho provo amb:

```bash
animeflv.com
```  

![alt text](img/image-44.png)

Pero si introduim l'url introduïda a la whitelist, veurem com ens deixarà accedir.

```bash
animenewsnetwork.com
```

![alt text](img/image-45.png)

### Bloqueig per hores

Per configurar el bloqueig d'hores anem a filtratge d'url i a "control de acceso basado por tiempo". Allà introduïm els marges que vulguem i guardem.

![alt text](img/image-46.png)
![alt text](img/image-47.png)

Si anem a fer una búsqueda qualsevol, veurem que no podem fer-ho dins les hores indicades.