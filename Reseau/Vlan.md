# Creation de Vlan - Cisco Packet Tracer

### Introduction 

[Vidéo de documentation](https://www.youtube.com/watch?v=ze5uAhy0ETI)

Créer une vlan permet de séparer les réseaux même si les appareils sont connectés sur un switch. Si donc deux appareils sont connectés sur un switch mais ne sont pas dans la même vlan, ils ne pourront pas commuiquer entre eux.

### Rappel
La touche __?__ est l'équivalent du help, et peut servir pour afficher la liste des commandes

### Liste des commandes

1. Mettre les IP dans le même réseau 
   - Ex : pc 1 -> 192.168.1.100 / pc 2 -> 192.168.1.101

2. Connecter les pc au switch avec un cable simple
    - Tester la connexion avec un ping

3. Dans le switch
    - Tous les ports devraient être dans le vlan 1
```sh
show vlan
```

4. Creation de Vlan
    - Dans le switch
```sh
en
conf t
vlan 10 <numero vlan>
# Optionel, donner un nom
name <nom>
```

5. Ajout des ports dans un vlan
    - Dans un switch
```sh
en
conf t

# Changer un port
interface <nom de l'interface> <numero du port>
# Ex : interface fastEthernet 0/1

# Changer plusieurs ports à la fois
interface range fastethernet 0/<premier port>-<dernier port>
# Ex : interface range fastethernet 0/1-20

switchport access vlan <numero vlan>

```

6. Configuration de l'adresse IP de la vlan
    - Dans un switch
```sh
en
conf t

interface vlan <numero de la vlan>

# Changement de l'addresse IP de la vlan
ip address 192.168.99.2
no shut
```

---

## Documentation Nathan

Vlan crée par default :
	Vlan1 
		- Port par défaut : touts les ports du switch
		- une fois configurer -> attribuer les ports 
Avoir des vlan diffèrent permettant d'avoir deux réseau diffèrent sur le même switch 
Trunck : tag les différents vlan pour les relier les différents vlan

Annuler la translation DNS :
```Cisco
enable
config
No ip domain lookup
```
Crée un Vlan :

```cisco
config
Vlan *numéro*
name "nom du vlan"
end
```

Attribuer des ports :

```Cisco
config
interface range fastethernet 0/*port*-*fin de range* 
switchport access vlan *numéro du vlan*
end
```

Mettre un port en mode trunk :
```Cisco
config 
interface fastethernet 0/*numero du port*
switchport mode trunk
end
```

Afficher les vlan :

```cisco
show vlan brief
```