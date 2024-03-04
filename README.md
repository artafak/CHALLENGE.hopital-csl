# CHALLENGE Hopital-csl.fr
VM de challenge pour tester ses compétences en Pentest...

![Présentation](https://i.ibb.co/FntHkDX/logo.jpg)

# Introduction

**hopital-csl** est la simulation d'un serveur utilisé au sein d'un centre hospitalier (l'hôpital de Chalans-sur-Loire). Inspiré des cyberattaques sur de nombreux hôpitaux ces dernières années, il est un exemple d'infrastructure proposant plusieurs services en adéquation avec les besoins actuels d'après pandémie COVID-19 : télétravail, consultation à distance, numérisation et partage des documents, centralisation... le tout avec une couche de sécurité censée prévenir les cyberattaques de plus en plus fréquentes et sophistiquées.

Pour permettre une polyvalence et élargir l'expérience au plus grand nombre, il est possible d'utiliser plusieurs voies et techniques pour arriver à en prendre le contrôle. Ce challenge peut ainsi s'adresser à des spécialistes des recherches en sources ouvertes qui relèveront tous les indices nécessaires, ou à des attaquants aguerris, soucieux d'exploiter des vulnérabilités qui sortent de l'ordinaire.


# Scénario

Le Centre Hospitalier de Chalans-Sur-Loire, situé à Ancenis dans le département de la Loire-Atlantique, offre des services de soins hospitaliers à une population de près de 10 000 personnes dans tout le pôle urbain d'Ancenis-Saint-Géréon.

L'année 2020, marquée par la pandémie de COVID-19 a été un tournant radical dans la gestion du personnel et des patients. Le personnel de l'hôpital devant continuer à travailler de façon dégradée malgré la crise et les risques encourus, le système informatique n'était pas conçu pour répondre aux besoins d'évolution :
- pas de possibilité de télétravail pour le personnel administratif non affecté aux soins des patients
- pas d'évolution possible
- pas de téléconsultation (consultation à distance)
- aucun suivi des patients par le personnel soignant à distance
- rédaction des ordonnances et arrêts de travail de manière non numérique (falsification possible)
- ...

Face à l'urgence de la situation, le chef de service avait mandaté une entreprise locale, CyberDream, pour mettre en place une infrastructure permettant de répondre aux besoins immédiats.

Nous sommes aujourd'hui en 2024 et le plus fort de la crise COVID-19 semble être derrière nous. Ce nouveau système est quotidiennement utilisé par tous les collaborateurs et personnels de l'hôpital, et même par des prestataires (associations, EHPAD...) ou des patients grâce au service de consultation en ligne TéléMédic.

Face aux différentes attaques cyber menées par des groupes de hackers sur des infrastructures de santé (hôpital de Villefranche-sur-Saône en février 2021, cité sanitaire de Saint-Nazaire le 12 Janvier 2022, hôpital de Corbeil-Essonnes le 26 Septembre 2022, et plus récemment celui de Versailles) le Gouvernement a lancé mi-2023 un "plan blanc numérique" pour doter les établissements de santé des réflexes et pratiques pour lutter contre les attaques cyber.

C'est dans ce cadre que vous intervenez. Mandaté par le département sécurité numérique de la préfecture d'Ancenis, votre mission est d'auditer le système actuel pour déterminer sa robustesse et sa résilience en cas d'attaque, afin de savoir s'il peut être conservé en l'état, où si des aménagements sont nécessaires.

A savoir que l'ancien système informatique a été désactivé car il n'était plus maintenu à jour, l'équipe informatique avait été remerciée, faute de moyens suffisants dans les budgets précédents.
Des propres mots du référent sécurité informatique du CH-CSL : "_Une panne sur ce nouveau service nous ferait revenir à l'âge de pierre... ou plutôt du papier et du crayon, ce qui est tout bonnement impensable !__"


# Technique
### Scénario du point de vue technique

Vous allez auditer le serveur principal de l'infrastructure. C'est le serveur installé par le prestataire CyberDream.
Une machine virtuelle en format OVA 2.0 utilisable avec VirtualBox (7.x)
La machine virtuelle dispose des caractéristiques suivantes :
RAM : 2Go (nécessaires).  4Go (confort)
Espace disque nécessaire : environ 10 Go max.  (La VM fait 6,5Go)
Une carte réseau virtuelle

La machine d'attaque, si elle est sur le même réseau, recevra directement une IP lui permettant de joindre le serveur ciblé.

# Mise en place 

### Importation

![Présentation](https://i.ibb.co/3WjLxTC/Pasted-image-20240129150207.png)

### Configuration

La VM doit être configurée pour permettre à la carte réseau de communiquer avec le **réseau privé hôte** de VirtualBox.

![Présentation](https://i.ibb.co/gwnydsy/Pasted-image-20240115111857.png)

(Elle est par défaut configurée pour avoir ce paramétrage)
Pour les besoins du scénario, la machine virtuelle peut disposer d'un accès à Internet (c'est facultatif). Néanmoins, aucune ressource sur Internet n'est essentielle pour le fonctionnement normal du serveur.


# Flags et indices

Il y a 8 flags à récupérer tout au long de ce challenge.
- 1 : les mails sont nos amis
- 2 : Attention à ce que vous commentez
- 3 : You want my cookies ? yes ! EAT MY COOKIES !
- 4 : Le numéro de téléphone de la direction de l'hôpital, toujours utile pour du social engineering
- 5 : Le VPN, réel besoin pour le télétravail ou porte d'entrée ouverte aux attaquants ?
- 6 : Besoin d'une consultation à distance ? pensez TéléMédic !
- 7 : CV de l'admin système, c'est intéressant !
- 8 : Besoin d'une radio des poumons ?

Les 8 flags réunis vous donneront une surprise...

Le bruteforce n'est ni utile, ni nécessaire pour l'ensemble du challenge. inutile de perdre votre temps. Les mots de passe sont robustes.


# Crédits

Simulation créée par Artafak (artafak@yahoo.fr) en janvier 2024 au profit de la formation ESD (Expert en sécurité digitale : https://esdacademy.eu)
Le site Internet _hopital-csl.fr_ de la simulation a été grandement inspiré par celui du centre hospitalier d'Erdre et Loire (_ch-erdreloire.fr_) dont certains éléments ont été utilisés. Les documents, fichiers et images utilisés dans le scénario, bien que récupérés depuis le-dit site, ont été modifiés afin de changer les noms, prénoms, photos et éléments permettant l'identification formel de l'hôpital d'Erdre-et-Loire (numéro de téléphone, adresse ...) uniquement dans le but de rendre la simulation plus immersive et réelle. Tous les noms des personnels apparaissant dans les documents ont été modifiés et sont purement fictifs. Tous les éléments utilisés dans le cadre de ce scénario appartiennent à leurs auteurs respectifs et ne peuvent être utilisés dans un cadre commercial. **Cette simulation ainsi que tous ses éléments ne sont utilisables que dans un domaine strictement pédagogique.** 
