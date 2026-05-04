# Challenge A1E09 - Adressage IP


##### Consignes

Pour les adresses IP et masques de sous-réseau suivants, calculez :

* l’adresse de réseau
* l’adresse de broadcast
* le nombre d’adresses utilisables par des machines
* la plage d’adresses disponibles
  
    
## 192.168.13.67/24
  

Adresse IP : `192.168.13.67/24`   
Masque : `255.255.255.0`  

Ici pas besoin de faire de calcul puisque le masque se termine sur un octet.  
L'**adresse réseau** est donc `192.168.13.0`.  
L'**adresse de broadcast** `192.168.13.255`.  
La **plage d'adresses disponibles** va de `192.168.13.1` à `192.168.13.254`.  
Le **nombres d'adresses disponibles** est de *254*.    
  

## 172.16.0.1 – 255.255.255.0  

Adresse IP : `172.16.0.1`    
Masque : `255.255.255.0`  

Ici aussi le masque se termine sur un octet, pas besoin de faire de calcul  
L'**adresse réseau** est donc `172.16.0.0`  
L'**adresse de broadcast** `172.16.0.255`  
La **plage d'adresses disponibles** va de `172.16.0.1` à `172.16.0.254`  
Le **nombres d'adresses disponibles** est de *254*.    


## 172.16.27.32/23

Adresse IP :

* décimal : `172.16.27.32`
* binaire : `1010 1100.0001 0000.0001 1011.0010 0000`  

Masque :
* décimal : `255.255.254.0`
* binaire : `1111 1111.1111 1111.1111 1110.0000 0000`


### Utilisation de la technique du nombre magique :

Octet significatif : 254  
Nombre magique 256-254 = 2

Multiplicateurs de 2 jusqu'à dépasser la valeur de l'octet significatif sur l'adresse IP :  
0;2;4;6;8;10;12;14;16;18;20;22;24;26;28 ...

Remplacement de l'octet de l'IP par le plus grand plus petit des multiplicateurs puis passage des octets suivant à 0 pour trouver l'adresse réseau :

**Adresse réseaux** : `172.16.26.0`

Pour trouver l'adresse de broadcast on remplace l'octet par le multiple suivant -1 et on passe les octets suivants à 255 :

**Adresse de broadcast** : `172.16.27.255`

La **plage d'adresses disponibles** va de `172.16.26.1` à `172.16.27.254`.

**Nombre d'adresses disponibles** : Nombre de bits disponible pour l'hôte-2 : (9^2)-2 = *510*.



### Utilisation de la méthode classique :

###### Détermination de l'adresse réseau :

Utilisation du AND logique pour déterminer l'adresse réseau :  
| IP :             | `1010 1100.0001 0000.0001 1011.0010 0000` |  
|:-|:-|
| Masque :         | `1111 1111.1111 1111.1111 1110.0000 0000` |  
| Adresse réseau : | `1010 1100.0001 0000.0001 1010.0000 0000` |  

***Adresse réseau* en décimal** : `172.16.26.0`

###### Détermination de l'adresse de broadcast :

Utilisation du NOT logique sur le masque :  
`0000 0000.0000 0000.0000 0001.1111 1111`

Utilisation du OR logique entre le masque inversé et l'adresse IP :

|IP :        |`0000 0000.0000 0000.0000 0001.1111 1111`| 
|:-|:-| 
|Masque :    |`1010 1100.0001 0000.0001 1011.0010 0000`|  
|Broadcast : |`1010 1100.0001 0000.0001 1011.1111 1111`|

**Adresse de broadcast** en décimal : `172.16.27.255`


## 10.7.5.1 – 255.255.128.0

Adresse IP :

* décimal : `10.7.5.1`
* binaire : `0000 1010.0000 0111.0000 0101.0000 0001`  

Masque :
* décimal : `255.255.128.0`
* binaire : `1111 1111.1111 1111.1000 0000.0000 0000`

### Utilisation de la technique du nombre magique :
Octet significatif : 128  
Nombre magique 256-128=128

Multiplicateurs de 128 jusqu'à dépasser la valeur de l'octet significatif sur l'adresse IP :  
0;128;

Remplacement de l'octet de l'IP par le plus grand plus petit des multiplicateurs puis passage des octets suivant à 0 pour trouver l'adresse réseau :

**Adresse réseaux** : `10.7.0.0`

Pour trouver l'adresse de broadcast on remplace l'octet par le multiple suivant -1 et on passe les octets suivants à 255 :

**Adresse de broadcast** : `10.7.127.255`

La **plage d'adresses disponibles** va de `10.7.0.1` à `10.7.127.254`

**Nombre d'adresses disponibles** : Nombre de bits disponible pour l'hôte-2 : (2^15)-2 = *32 766*.

### Utilisation de la méthode classique :

###### Détermination de l'adresse réseau :

Utilisation du AND logique pour déterminer l'adresse réseau :  
|IP :             |`0000 1010.0000 0111.0000 0101.0000 0001`|
|:-|:-|
|Masque :         |`1111 1111.1111 1111.1000 0000.0000 0000`|  
|Adresse réseau : |`0000 1010.0000 0111.0000 0000.0000 0000`|

**Adresse réseau** en décimal : `10.7.0.0`

###### Détermination de l'adresse de broadcast :

Utilisation du NOT logique sur le masque :  
`0000 0000.0000 0000.0111 1111.1111 1111`

Utilisation du OR logique entre le masque inversé et l'adresse IP :

|IP :        |`0000 1010.0000 0111.0000 0101.0000 0001`| 
|:-|:-|
|Masque :    |`0000 0000.0000 0000.0111 1111.1111 1111`|  
|Broadcast : |`0000 1010.0000 0111.0111 1111.1111 1111`|

**Adresse de broadcast** en décimal : `10.7.127.255`



## 10.42.0.82/12

Adresse IP :

* décimal : `10.42.0.82`
* binaire : `0000 1010.0010 1010.0000 0000.0101 0010`  

Masque :
* décimal : `255.240.0.0`
* bnaire : `1111 1111.1111 0000.0000 0000.0000 0000`

### Utilisation de la technique du nombre magique :
Octet significatif : 240  
Nombre magique 256-240=16

Multiplicateurs de 16 jusqu'à dépasser la valeur de l'octet significatif sur l'adresse IP :  
0;16;32;48



Remplacement de l'octet de l'IP par le plus grand plus petit des multiplicateurs puis passage des octets suivant à 0 pour trouver l'adresse réseau :

**Adresse réseaux** : `10.32.0.0`

Pour trouver l'adresse de broadcast on remplace l'octet par le multiple suivant -1 et on passe les octets suivants à 255 :

**Adresse de broadcast** : `10.47.255.255`

La **plage d'adresses disponibles** va de `10.32.0.1` à `10.47.255.254`

**Nombre d'adresses disponibles** : Nombre de bits disponible pour l'hôte-2 : (2^20)-2 = **1 048 574**.  


### Utilisation de la méthode classique :

###### Détermination de l'adresse réseau :

Utilisation du AND logique pour déterminer l'adresse réseau :  
|IP :             |`0000 1010.0010 1010.0000 0000.0101 0010`|  
|:-|:-|
|Masque :         |`1111 1111.1111 0000.0000 0000.0000 0000`|  
|Adresse réseau : |`0000 1010.0010 0000.0000 0000.0000 0000`|

**Adresse réseau** en décimal : `10.32.0.0`

###### Détermination de l'adresse de broadcast :

Utilisation du NOT logique sur le masque :  
`0000 0000.0000 1111.1111 1111.1111 1111`

Utilisation du OR logique entre le masque inversé et l'adresse IP :  

|IP :        |`0000 1010.0010 1010.0000 0000.0101 0010`|
|:-|:-|
|Masque :    |`0000 0000.0000 1111.1111 1111.1111 1111`|  
|Broadcast : |`0000 1010.0010 1111.1111 1111.1111 1111`|  

**Adresse de broadcast** en décimal : `10.47.255.255`

