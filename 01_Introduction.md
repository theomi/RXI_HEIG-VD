# Les réseaux informatiques
## Définition
Ensemble interconnecté d'ordinateurs autonome, utilisant un réseau à commutation pour l'interconnexion.
## Types de réseaux
Selon leur taille, l'étendue géographique détermine la technologie appropriée.
| Acronyme       | Nom                   | Distance | Exemples            | Technologies             |
|----------------|-----------------------|----------|---------------------|--------------------------|
|**`PAN`**       | Personal Area Network | 1 – 10m  | Périphériques<br>Gadgets personnels interconnectés<br>Home cinéma<br>Paiement électronique avec mobile<br>Ticket électronique<br>Echange de données entre mobiles | Bluetooth<br>Infrarouge<br>USB<br>ZigBee<br>NFC<br>RFID |
|**`LAN`**       | Local Area Network    | 1m – 1km | Réseau d'une entreprise dans un bâtiment ou un campus<br>Réseau wifi (domicile ou public) | Ethernet<br>Wifi |
|**`MAN`**       | Metropolitan Area Network | 1 - 10km  | Réseau d'un opérateur dans une ville<br>Réseau privé d'une entreprise dans un grand campus | Fibres optiques<br>Metro-Ethernet<br>WiMax|
|**`WAN`**      | Wide Area Network | 10 - 1000km  | Réseau national d'un opérateur<br>Réseau international d'un opérateur spécialisé | Fibres optiques<br>Faisceaux hertziens<br>Satellites |
|**`Internet`**      | Réseau des réseaux | Toute la planète  | Interconnexion des réseaux d'entreprises, réseaux académiques, réseaux des opérateurs, réseaux privés | Toutes les technologies, selon le réseau particulier

## Topologie des réseaux
Représente l'architecture du réseau, la disposition des nœuds et la structure des connexions entre les nœuds.

### Bus
* Tous les nœuds sont connectés au même médium (câble coax, canal radio)
* Une seule transmission est possible à chaque instant
* Utilisé dans les réseaux sans fil, les premiers LAN, les bus dans les ordinateurs (USB, PCI, SCSI...)

### Anneau
* Un segment de câble connecte deux stations
* Propagation active du signal autour de l'anneau
* Résilience contre les pannes d'un lien
* Utilisé dans les réseaux optiques, les premiers LAN

### Etoile
* Chaque station est connectée à un noœud central
* Le nœud central transmet les données reçues
  * à toutes les stations (similaire à un bus)
  * ou aux stations concernées
* Utilisée dans les LAN modernes

### Maillée
* Complètement maillée : interconnexion entre tous les nœuds
* Maillage partiel dans les réseaux réalistes
* Bonne tolérance aux pannes
* Utilisée dans les WAN sur fibre optique

## Commutation
C'est le processus d'acheminement des données à travers un réseau.

### Commutation de circuits
* Etablissement d'un cicruit par des commutateurs avant la transmission des données
* Transmission d'un signal analogique ou d'un flux continu de bits
* Utilisé dans les réseaux téléphoniques
  * Etablissement du circuit est rapide par rapport à la conversation
  * Qualité et délai de transmission constants
* Mal adapté aux réseaux informatiques
  * Courts échanges de données avec pauses longues

### Commutation de paquets
* La source segmente le message à transmettre en paquets
* Les éléments du réseau transmettent les paquets l'un après l'autre de manière indépendante
* Le destinataire recombine les paquets reçus pour obtenir le message

#### Avantages
* Utilisation économique de la ligne (mutualisation des ressources)
* Reroutage facile encas de panne d'un lien
* Conversion des formats possible

#### Inconvénients
* Délai de transfert variable et plus long
* Pertes de paquets possibles
* Nœuds intermédiaires doivent effectuer des opérations complexes

## Paramètres de performances
|Paramètre|Symbole|Exemple|Unités|
|---------|-------|-------|------|
|Délai    |**`t`**      |Délai aller-retour<br>Délai de transmission|1 s<br>1 ms = 1/1000 s = 10⁻³ s|
|Vitesse  |**`v`**      |Vitesse de propagation|1 m/s<br>1 km/s = 1000 m/s = 10³ m/s|
|Longueur de données|**`l`**      |Taille d'un paquet<br>Taille d'un fichier|1 B<br>1 KiB = 1024 B = 2¹⁰ B<br>1 MiB = 1024 KiB = 2²⁰ B<br>1 GiB = 1024 MiB = 2³⁰ B<br>1 TiB = 1024 GiB = 2⁴⁰ B|
|Débit binaire|**`r`**      |Débit de transmission|1 b/s<br>1 kb/s = 1000 b/s = 10³ b/s<br>1 Mb/s = 1000 kb/s = 10⁶ b/s<br>1 Gb/s = 1000 Mb/s = 10⁹ b/s<br>|
|Taux de perte|**`p`**      |Taux de perte de paquets|Pas d'unité<br>1% = 0.01 = 1/100 = 10⁻²|

## Délai de transmission

### Définition
Délai pour mettre les bits sur le médium.
### Calcul
#### `tₜᵣₐₙₛₘᵢₛₛᵢₒₙ = n / r`

`n : longueur du paquet [b]`
`r : débit binaire du lien [b/s]`

### Exemple (Wi-Fi) :
```
n = 500 B
r = 54 Mb/s = 54 * 10⁶ b/s
tₜᵣₐₙₛₘᵢₛₛᵢₒₙ = 500B * 8b/B / 54 * 10⁶ b/s
  = 74 * 10⁻⁶ s
  = 74 µs
```

## Délai de propagation

### Définition
Délai du signal physique entre émetteur et récepteur.
### Calcul
#### `tₚᵣₒₚ = L / vₚᵣₒₚ`

`L : longueur du lien (ou distance)`
`vₚᵣₒₚ : Vitesse de propagation`

### Exemple (Wi-Fi) :
```
L = 10 m
vₚᵣₒₚ = 300'000 km/s = 3 * 10⁸ m/s
tₚᵣₒₚ = 10 m / 3 * 10⁸ m/s
  = 3.33 * 10⁻⁸ s = 33.3 * 10⁻⁹ s
  = 33.3 ns
```
## Délai de traitement

### Définition
Délai de calcul nécessaire à un nœud.
* Vérification de la somme de contrôle
* Recherche dans la table de routage
* ...

### Calcul
* Dépend du nœud et des opérations à effectuer.
* Généralement très faible par rapport aux autres délais.

## Délai d'attente

### Définition
Délai d'attente dans la file d'attente de l'interface de sortie

### Calcul
#### `tₐₜₜₑₙₜₑ = Σᵢ nᵢ / r`

`Σᵢ nᵢ : Somme des longueurs de tous les paquets devant le paquent considéré`
`r : Débit binaire du lien`

### Exemple
```
tₐₜₜₑₙₜₑ = 10 * 500B * 8 b/B / 10 Mb/s
         = 4'000 * 10⁻⁶ s
         = 4 ms
```
## Délai de transit

### Définition
Temps total entre l'émission du premier bit par la source et la réception du dernier bit par le récepteur final

### Calcul
Somme de tous les délais sur tous les liens

