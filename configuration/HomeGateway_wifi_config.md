# Configuration Wi-Fi — Home Gateway1 (extension IoT)

Contrairement à R1/R2/SW1/SW2, le Home Gateway1 (DLC100) ne se configure pas en ligne de commande mais via son interface graphique (onglet **Config** dans Packet Tracer). Voici les réglages appliqués.

## Onglet Config → Wireless

| Paramètre | Valeur |
|---|---|
| SSID | `TogoTech_IoT` |
| Authentification | WPA2-PSK |
| Passphrase | `IoTSecure2026` |
| Type de chiffrement | AES |
| Canal | 6 - 2.437GHz |

## Onglet Config → Internet

| Paramètre | Valeur |
|---|---|
| Configuration IP | DHCP (obtenue depuis R1, pool `VLAN70_IoT`) |
| Adresse obtenue | 192.168.70.11 |
| Passerelle | 192.168.70.1 |
| DNS | 192.168.50.10 |

## Appareils connectés en Wi-Fi

Chaque appareil IoT (Motion Detector, Fan, Light, Door, Air Conditioner) est configuré individuellement dans son onglet **Config → Wireless0** avec le même SSID et la même passphrase :

- SSID : `TogoTech_IoT`
- Authentification : WPA2-PSK
- Passphrase : `IoTSecure2026`
- Adressage IP : DHCP (attribué par le Home Gateway, réseau interne géré par NAT — distinct du sous-réseau 192.168.70.0/24 vu par le reste de l'entreprise)

## Point de sécurité observé pendant les tests

Le Home Gateway applique un filtrage firewall par défaut sur les requêtes ICMP entrantes (ping) venant du réseau de l'entreprise — comportement standard d'un routeur domestique qui protège son réseau interne, y compris depuis un réseau qui lui est nominalement "de confiance". Ce comportement a été observé et documenté plutôt que désactivé, car il illustre une couche de défense supplémentaire cohérente avec l'objectif de sécurité du projet.
