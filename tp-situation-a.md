# Remplacement d'un switch d'étage saturé

[← Retour au portfolio](tp-camille.html)

*PME de métallurgie, 45 postes, site principal — mars 2026 — option SISR*

## Contexte

Le site principal compte 45 postes, dont 12 dans l'atelier, reliés à un switch d'étage installé en 2016. Les postes de l'atelier servent aux plans de fabrication et à la saisie des temps.

## Problématique

Depuis trois semaines, les 12 postes de l'atelier subissaient des coupures réseau de quelques secondes, plusieurs fois par jour. La sauvegarde du serveur de fichiers, lancée à 12 h, durait 42 minutes au lieu des 6 minutes habituelles et terminait parfois en erreur.

## Démarche

J'ai d'abord relevé les débits depuis un poste de l'atelier : 8 Mo/s en copie vers le serveur, contre 74 Mo/s depuis un poste du bureau. Trois hypothèses : le câblage, la carte réseau des postes, le switch.

J'ai écarté le câblage : les liens ont été certifiés en 2023 et un test au testeur de câble sur trois prises n'a rien montré. J'ai écarté la carte réseau : le problème touchait les 12 postes, pas un seul.

Restait le switch, un modèle 16 ports à 100 Mb/s dont les compteurs affichaient des erreurs de collision. Je l'ai remplacé par un switch administrable gigabit prêté par le fournisseur, pour valider l'hypothèse avant tout achat.

## Outils mobilisés

- Switch administrable 16 ports gigabit (modèle de prêt, puis modèle acheté)
- Testeur de câble RJ45
- Wireshark 4.2 pour observer les retransmissions
- GLPI 10.0 pour le suivi du ticket et la mise à jour de l'inventaire

## Précautions prises

J'ai sauvegardé la configuration de l'ancien switch, étiqueté les 16 câbles avant de les débrancher, et programmé l'intervention entre 12 h 30 et 13 h 15, hors production. J'ai prévenu le chef d'atelier la veille.

## Résultats

Le débit de copie est passé de 8 Mo/s à 74 Mo/s. La sauvegarde est redescendue à 6 minutes. Aucune coupure signalée dans les trois semaines qui ont suivi. L'inventaire GLPI a été mis à jour le jour même.

## Bilan personnel

J'ai perdu deux jours à suspecter le câblage alors que les compteurs d'erreurs du switch donnaient la réponse dès le premier relevé. La prochaine fois, je commencerai par interroger les équipements réseau en SNMP avant de tester les liens un par un.

---

**Compétences mobilisées** : gérer le patrimoine informatique ; répondre aux incidents et aux demandes d'assistance.


## Situation B:

## Contexte :

Le bureau d'études compte 8 postes de travail haute performance. L'un d'eux, une station Dell Precision 3660 dédiée à la modélisation 3D, présentait des dysfonctionnements critiques depuis deux semaines.

## Problématique :

Le poste subissait 3 à 4 redémarrages intempestifs par jour, entraînant la perte systématique des travaux en cours de l'utilisateur. L'observateur d'événements affichait des erreurs critiques récurrentes Kernel-Power 41.

## Démarche :

J'ai d'abord émis l'hypothèse d'un problème logiciel ou système : j'ai appliqué toutes les mises à jour Windows, mais les coupures ont persisté. J'ai ensuite suspecté la mémoire vive : j'ai exécuté un test Memtest86 durant une nuit complète, qui a révélé 0 erreur, écartant ainsi la RAM.

En inspectant le boîtier, j'ai constaté un encrassement important du bloc d'alimentation et un bruit anormal du ventilateur. Une mesure à la prise wattmétrique a révélé une consommation en pointe de 310 W pour une alimentation d'origine de 350 W, soit un fonctionnement à la limite de sa capacité maximale. J'ai donc décidé de remplacer le composant.

## Outils mobilisés :

Prise wattmétrique monophasée

Clé USB bootable Memtest86 v10.6

Alimentation Corsair RM550x (550 W, certification 80 PLUS Gold)

Bombes d'air sec et kit de tournevis de précision

## Précautions prises :

Avant toute ouverture du boîtier, j'ai éteint le poste, débranché le cordon d'alimentation secteur, puis appuyé 5 secondes sur le bouton d'allumage pour décharger les condensateurs. J'ai également utilisé un bracelet antistatique pour éviter toute décharge électrostatique sur les composantes internes.

## Résultats :

Le remplacement par l'alimentation de 550 W et le dépoussiérage du boîtier ont résolu le problème. En 30 jours de suivi après intervention, aucun redémarrage intempestif n'a été constaté et 100 % de la stabilité du poste a été restaurée.

## Bilan personnel :

J'ai perdu du temps à chercher une cause logicielle alors qu'une inspection visuelle et matérielle dès le début m'aurait orienté plus rapidement vers l'alimentation. Pour les prochains incidents de ce type, j'intégrerai systématiquement le contrôle de l'alimentation et un nettoyage matériel dans mes premières vérifications.

Compétences mobilisées : gérer le patrimoine informatique ; répondre aux incidents et aux demandes d'assistance.
