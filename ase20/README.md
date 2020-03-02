# TP2: Configuration réseau 

Il s'agit ici de la réalisation d'un tp d'administration système.

## Configuration : set_network.sh

Ce script sert à réaliser la configuration réseau de la machine avec des données fournis dans des fichiers.

### Prérequis

Avant d'executer le script il faut créer les fichiers **machines** et **param** contenant les éléments suivant :

```
$cat machines

192.168.56.101 serveur
192.168.56.102 client
192.168.56.103 esclave

```
Le fichier machines comprends le nom des machines et leur adresse IP associée.

```
$cat param

MACHINE_LISTE=machines
IF=enp0s3
DOMAINE_IP="ubo.local"

```
Le fichier param contient le chemin du fichier précédent, l'interface réseau à configurer et le nom de domaine. 

### Utilisation

Le script doit être utiliser avec un utilisateur ayant les droit nécéssaires pour modifier les fichiers de configuration réseau de la machine.

```
$ sudo ./set_network.sh client
192.168.56.102 client
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0

```

Le script va configurer l'interface réseau avec l'adresse IP et le Hostname de la machine fournis en paramètre, ici client.

Si tout se passe bien le script affiche 0 partout.

## Vérification : verify_network.sh

Ce script sert à vérifier la bonne execution du script précédent.

### Prérequis

Pour pouvoir faire les vérification il faut avoir lancer le script set_networt.sh sur au moins deux machine d'un même réseau.

**Machine 1 :**

```
$ sudo ./set_network.sh client
192.168.56.102 client
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0

```

**Machine 2 :**

```

$ sudo ./set_network.sh serveur
192.168.56.101 serveur
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
0
```



### Utilisation

Le script va réaliser un ping vers la cible demandé et vérifier si les paramètres réseau ont bien été bien configuré par **set_network.sh**

```
$ sudo ./verify_network.sh serveur

Ping vers cible :
Ping vers serveur réussi

Vérification des variables réseau :
Variable BOOTPROTO -> ok
Variable GATEWAY -> ok
Variable IPADDR -> ok
Variable PREFIX -> ok

```

La commande précédente à été faite depuis la machine 1.


## Auteurs

* **Yvonnou Théo** - *Réalisation des scripts* - Master I TIIL-A


