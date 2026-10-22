# Nexus Compression & Recovery Studio — Accueil

**2.7.0 · Français**

Cette page est la source du wiki à relire pour la prochaine version. Elle ne signifie pas que le wiki public ou la version d’essai en ligne est déjà publié.

[English](Home.md) · [Français](Home.fr.md) · [日本語](Home.ja.md) · [한국어](Home.ko.md)

## Objectif

Explorez la compression factorisée à faible précision et la récupération guidée par un modèle enseignant. Compression, inférence réussie et qualité récupérée sont des étapes distinctes. Choisissez un modèle et un corpus locaux compatibles. Le ZIP du corpus original est sélectionné localement et vérifié par somme de contrôle ; il n’est pas intégré au HTML.

## Choisir une édition

### Édition navigateur

[HTML](../../Nexus_Compression_Recovery_Studio_v2_7_Browser.html) · [README](../../README.md)

Utilisez un navigateur compatible WebGPU en HTTPS ou sur une origine localhost sécurisée prise en charge. Le fichier HTML unique contient le moteur JavaScript/WGSL personnalisé. Importez des fichiers locaux compatibles. Python, PyTorch, les services natifs, le téléchargement de jeux de données en ligne et la télémétrie GPU native ne sont pas disponibles ; les requêtes réseau de l’application sont bloquées. L’affichage du code sur GitHub n’exécute pas l’application.

### Édition installée

Extrayez le ZIP complet et gardez l’installateur avec toutes ses parties de données. Chaque composant distribué doit faire moins de 20 000 000 octets ; les fichiers reconstruits et les modèles téléchargés peuvent être plus volumineux. Suivez le manifeste et le récapitulatif de l’installateur de cette version. Les réglages et tests PyTorch natifs concernent l’édition installée, pas l’édition HTML seule.

## Mesures et limites

Les tests CPU et les contrôles statiques/DOM ne valident pas l’exécution sur du matériel Windows/Radeon/WebGPU réel. Comparez uniquement des conditions équivalentes : modèle, corpus, contexte, lot, précision et moteur. Les débits d’entraînement, de récupération, de traitement des invites et de génération sont des mesures différentes. Aucune compatibilité universelle ni vitesse maximale n’est garantie.

Débit de récupération enregistré, déclaré par le développeur : **2 500 jetons/seconde**. Il n’a pas été reproduit indépendamment ici et ne mesure pas la génération conversationnelle. Ce travail Nexus indépendant s’inspire de LittleBit de Samsung Research ; il ne s’agit pas d’une version officielle Samsung. Un stockage sous un bit ne prouve ni une mémoire d’entraînement sous un bit ni une résidence dans le cache L3. Conservez les licences applicables, dont CC BY-NC 4.0 pour le code SamsungLabs LittleBit.

## Crédits et licences

Rich Dunbar / Nexus Emerging Technology, avec l’aide d’outils de codage par IA. Les licences existantes et les conditions applicables aux recherches, au code, aux modèles et aux données tiers restent en vigueur. Cette page n’accorde aucune licence supplémentaire.
