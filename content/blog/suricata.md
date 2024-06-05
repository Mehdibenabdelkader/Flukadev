---
title: "Suricata"
date: 2024-06-05T01:55:24+01:00
draft: true
---

# Partie 1: Introduction

Dans le paysage numérique actuel, protéger l'infrastructure réseau contre les cybermenaces est crucial. Les systèmes de détection d'intrusion (IDS) jouent un rôle vital dans l'identification et la mitigation de ces menaces. Suricata, un puissant moteur IDS/IPS/NSM open-source, est largement utilisé pour la détection des menaces réseau en temps réel. Ce rapport fournit un guide complet pour configurer un IDS à l'aide de Suricata, détaillant chaque étape et expliquant la fonctionnalité des différentes commandes.

# Qu'est-ce que Suricata?

Suricata est un moteur avancé de détection des menaces réseau open-source développé par l'Open Information Security Foundation (OISF). Il fonctionne comme un système de détection d'intrusion (IDS), un système de prévention des intrusions (IPS) et un outil de surveillance de la sécurité réseau (NSM). Suricata est capable d'inspection approfondie des paquets, de détection d'anomalies basée sur les flux et d'utilisation de règles externes pour détecter les activités malveillantes. Il prend en charge divers protocoles et fournit une détection des menaces performante et évolutive.

# Comparaison détaillée : IDS vs. IPS

**Système de Détection d'Intrusion (IDS)**

- **Fonction** : Surveille le trafic réseau pour détecter des activités suspectes et alerte les administrateurs.
- **Types** : Basé sur le réseau (NIDS) et basé sur l'hôte (HIDS).
- **Mode** : Passif ; ne bloque ni ne prévient les menaces.
- **Déploiement** : Souvent placé à un point de surveillance du réseau pour observer le trafic.
- **Exemple** : Suricata en mode IDS.

**Système de Prévention d'Intrusion (IPS)**

- **Fonction** : Surveille et empêche ou bloque activement les menaces détectées.
- **Types** : Basé sur le réseau (NIPS) et basé sur l'hôte (HIPS).
- **Mode** : Actif ; peut bloquer et atténuer les menaces en temps réel.
- **Déploiement** : En ligne avec le trafic réseau pour intercepter et analyser les paquets.
- **Exemple** : Suricata configuré pour bloquer le trafic malveillant.

**Différences Clés**

- **Activité** : L'IDS ne fait que détecter et alerter, tandis que l'IPS détecte et bloque.
- **Impact sur le Trafic** : L'IDS n'a aucun impact direct sur le flux de trafic ; l'IPS peut affecter le flux de trafic en raison de sa nature active.
- **Cas d'Utilisation** : L'IDS est utilisé là où la visibilité est nécessaire sans intervention, tandis que l'IPS est utilisé dans des environnements nécessitant une atténuation active des menaces.

# Partie 2 : Installation et Configuration de Suricata

#### 1. Mise à Jour du Système
```sh
sudo apt-get update
sudo apt-get upgrade
```
- **Explication** : Ces commandes mettent à jour la liste des paquets disponibles et mettent à jour tous les paquets installés vers leurs dernières versions.

#### 2. Installation de Suricata
```sh
sudo apt-get install suricata
```
- **Explication** : Cette commande installe Suricata à partir des dépôts officiels.

#### 3. Configuration de l'Interface Réseau
Éditez le fichier de configuration principal de Suricata : `/etc/suricata/suricata.yaml`.

- **Chemin** : `/etc/suricata/suricata.yaml`
- **Contenu Important** :
  ```yaml
  af-packet:
    - interface: eth0
      cluster-id: 99
      cluster-type: cluster_flow
      defrag: yes
  ```
  - **Explication** : Cette configuration indique à Suricata de surveiller le trafic sur l'interface `eth0`.

#### 4. Téléchargement des Règles
```sh
sudo suricata-update
```
- **Explication** : Cette commande télécharge et met à jour les derniers ensembles de règles de la communauté Emerging Threats.

#### 5. Démarrage de Suricata
```sh
sudo systemctl start suricata
sudo systemctl enable suricata
```
- **Explication** : Ces commandes démarrent le service Suricata et le configurent pour qu'il démarre automatiquement au démarrage du système.

#### 6. Vérification de l'Installation
```sh
sudo suricata -V
```
- **Explication** : Cette commande vérifie l'installation de Suricata et affiche la version installée.

#### 7. Test de Suricata
Pour tester Suricata, vous pouvez utiliser des outils comme `nmap` pour générer du trafic de test et vérifier si Suricata le détecte et le journalise.

#### 8. Analyse des Logs
Les logs sont stockés dans `/var/log/suricata/`. Voici quelques fichiers importants :
- **fast.log** : Alertes rapides.
- **eve.json** : Logs détaillés en format JSON.
- **stats.log** : Statistiques de performance.

#### 9. Fichiers de Configuration et leur Utilité
- **`/etc/suricata/suricata.yaml`** : Fichier principal de configuration. Configure les interfaces réseau, les règles, les journaux, etc.
- **`/var/log/suricata/`** : Répertoire où Suricata stocke tous ses logs. Contient des fichiers comme `fast.log`, `eve.json`, et `stats.log` pour les alertes et les statistiques.

# Partie 3 : Tester Suricata avec `testmynids`

#### 1. Introduction à `testmynids`
`testmynids` est un script qui aide à tester les systèmes IDS comme Suricata en envoyant des modèles d'attaque connus et en observant s'ils sont détectés. Cet outil peut simuler diverses attaques pour s'assurer que Suricata est correctement configuré et opérationnel.

#### 2. Prérequis
Assurez-vous que Suricata est installé et en cours d'exécution sur votre système. Vérifiez également que `curl` est installé, car il est utilisé par `testmynids` pour envoyer des modèles de test.

#### 3. Télécharger `testmynids`
```sh
wget https://raw.githubusercontent.com/pevma/ids-rule-testing/master/testmynids.sh
chmod +x testmynids.sh
```
- **Explication** : La première commande télécharge le script `testmynids` à partir de l'URL spécifiée. La deuxième commande rend le script exécutable.

#### 4. Exécution du Script
```sh
./testmynids.sh
```
- **Explication** : Cette commande exécute le script `testmynids`. Le script enverra divers modèles de test à votre instance Suricata.

#### 5. Analyse des Logs de Suricata
Après avoir exécuté `testmynids`, vérifiez les journaux de Suricata pour voir si les attaques ont été détectées.
- **Emplacement des Fichiers de Log** : `/var/log/suricata/`
  - **fast.log** : Résumé rapide des alertes détectées.
  - **eve.json** : Entrées de log détaillées au format JSON.

#### 6. Commandes Exemples et Résultats Attendus
- **Vérification de `fast.log`** :
  ```sh
  cat /var/log/suricata/fast.log
  ```
  - **Explication** : Cette commande affiche le contenu de `fast.log`, où vous devriez voir des entrées correspondant aux attaques de test envoyées par `testmynids`.

- **Vérification de `eve.json`** :
  ```sh
  cat /var/log/suricata/eve.json | jq .
  ```
  - **Explication** : Cette commande utilise `jq` pour formater et afficher les journaux JSON de `eve.json`. Recherchez les entrées avec "alert" pour voir les détails des attaques détectées.

#### 7. Vérification de la Détection
Comparez les alertes dans `fast.log` et `eve.json` avec les résultats attendus du script `testmynids`. Chaque modèle de test envoyé par le script devrait correspondre à une alerte dans les journaux.

#### 8. Dépannage
- **Aucune Alerte Détectée** :
  - Vérifiez que Suricata fonctionne sur la bonne interface.
  - Vérifiez la configuration de `suricata.yaml`.
  - Assurez-vous que les ensembles de règles sont à jour avec `sudo suricata-update`.

# Partie 4: Étapes pour Configurer des Règles de Désactivation et de Suppression pour Réduire les Faux Positifs avec Suricata

#### 1. Introduction
Les faux positifs peuvent nuire à l'efficacité d'un IDS. Suricata permet de configurer des règles de désactivation et de suppression pour réduire ces alertes non pertinentes.

#### 2. Désactivation des Règles
- **Éditer le fichier `suricata.yaml`** :
  ```yaml
  default-rule-path: /etc/suricata/rules
  rule-files:
    - suricata.rules
    - disable.conf
  ```
  - **Explication** : Ajoutez `disable.conf` dans la liste des fichiers de règles.

- **Créer ou éditer `disable.conf`** :
  ```sh
  echo 'disable sid:<rule_id>' >> /etc/suricata/rules/disable.conf
  ```
  - **Explication** : Cette commande désactive la règle spécifiée par son ID (sid).

#### 3. Configuration des Règles de Suppression
- **Créer ou éditer `threshold.config`** :
  ```sh
  suppress gen_id 1, sig_id <rule_id>, track by_src, ip <ip_address>
  ```
  - **Explication** : Cette règle supprime les alertes pour la règle spécifiée (sig_id) provenant d'une adresse IP particulière.

#### 4. Redémarrer Suricata
```sh
sudo systemctl restart suricata
```
- **Explication** : Redémarre Suricata pour appliquer les nouvelles configurations.

#### 5. Vérification
- **Analyser les logs** :
  ```sh
  tail -f /var/log/suricata/fast.log
  ```
  - **Explication** : Surveillez les logs pour vérifier que les faux positifs sont réduits.

### Conclusion
ktbi conclusion l3ar