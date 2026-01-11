# 🚀 Exercice 02 : Gestion d’annuaire via Powershell

Ce dépôt contient les scripts et ressources utilisés pour la mise en place du domaine **laplateforme.io**.

## 📖 Présentation du projet
L’objectif de cet exercice est de déployer une infrastructure Active Directory complète de manière automatisée. Au lieu d'une configuration manuelle, l'intégralité du processus a été réalisée via PowerShell afin de :
* Réduire les erreurs humaines lors de la saisie des données.
* Garantir un gain de temps significatif pour l'import massif de collaborateurs.
* Assurer une traçabilité totale de la configuration du serveur.

## 🚀 Phases de déploiement

### 1. Installation du rôle AD DS et promotion du domaine
Le déploiement a commencé par la transformation du serveur vierge en contrôleur de domaine racine pour la forêt `laplateforme.io`.

**Commandes utilisées :**
* Installation des services : `Install-WindowsFeature -name AD-Domain-Services -IncludeManagementTools`
* Configuration de la forêt : `Install-ADDSForest -DomainName "laplateforme.io" -DomainNetBIOSName "LAPLATEFORME" ...`

### 2. Importation via Powershell
Une fois le domaine opérationnel, l'intégration des collaborateurs a été effectuée via le script `Import.ps1`. Ce script traite de manière itérative le fichier `Utilisateurs.csv` pour transformer les données brutes en objets Active Directory fonctionnels.

**Logique du script :**
* **Traitement itératif** : Lecture ligne par ligne du CSV pour garantir l'intégrité de chaque compte.
* **Structure hiérarchique** : Création des objets au sein d'une structure organisée.
* **Sécurité** : Application d'un mot de passe par défaut avec obligation de changement à la première connexion.



## 🔎 Vérification et Conformité
Après l'exécution, une phase de vérification rigoureuse a été menée via l’outil **« Utilisateurs et ordinateurs Active Directory »** pour confirmer :
* **La création des comptes** : Validation visuelle de la présence de tous les utilisateurs.
* **La gestion multi-groupes** : Vérification spécifique des appartenances multiples (exemple : Marc Thillot), prouvant la capacité du script à gérer plusieurs groupes par utilisateur.
