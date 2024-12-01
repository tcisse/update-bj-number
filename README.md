# Mise à Jour des Contacts avec Préfixe `01`

Ce projet est une application web qui permet de mettre à jour vos contacts téléphoniques en ajoutant automatiquement le préfixe `01` pour les numéros de téléphone au format béninois. L'application utilise un fichier `.vcf` (vCard) pour l'importation et l'exportation des contacts, en fournissant une interface utilisateur pour visualiser les changements avant validation.

---

## Fonctionnalités

- **Importation de contacts au format `.vcf`** :
  - Permet de charger un fichier `.vcf` contenant vos contacts existants.

- **Analyse des numéros à modifier** :
  - Identifie les numéros valides nécessitant l'ajout du préfixe `01`.
  - Affiche une liste des contacts affectés avant d'appliquer les changements.
  - Affiche le nombre total de contacts modifiés.

- **Visualisation des modifications** :
  - Présente une vue avant/après des numéros :
    - Nom du contact.
    - Ancien numéro.
    - Nouveau numéro.

- **Comptage des contacts affectés** :
  - Nombre total de numéros modifiés ou ajoutés.

- **Validation stricte des numéros** :
  - Les numéros doivent contenir exactement **8 chiffres** après suppression des espaces.
  - Les numéros déjà conformes (`01` en préfixe) ne sont pas modifiés.
  - Les numéros incomplets ou mal formatés (ex. `99`) sont ignorés.

- **Exportation des contacts mis à jour** :
  - Génère un fichier `.vcf` contenant les modifications validées.

---

## Cas Pris en Charge

1. **Numéros au format standard** :
   - Exemple : `94612855` devient `01 94 61 2855`.

2. **Numéros avec espaces** :
   - Exemple : `94 61 2855` devient `01 94 61 2855`.

3. **Numéros déjà conformes** :
   - Exemple : `01 94 61 2855` reste inchangé.

4. **Numéros incomplets ou invalides** :
   - Exemple : `99` est ignoré.

5. **Numéros avec différents formats** :
   - Numéros courts ou avec des caractères non numériques sont exclus.

6. **Numéros avec préfixe international `+229`** :
   - Si un numéro commence par `+229` et que la partie locale (après `+229`) ne commence pas par `01`, alors `01` est ajouté.
   - Exemple : `+22951220980` devient `+2290151220980`.
   - Les numéros déjà conformes (ex. `+2290151220980`) restent inchangés.

7. **Création de numéros secondaires** :
   - Ajoute un nouveau numéro basé sur la logique d'ajout du préfixe `01`.
   - Exemple : 
     - Ancien numéro : `94612855`
     - Numéro secondaire créé : `01 94 61 2855`

---

## Dépendances

- **Frontend** : Interface utilisateur développée en **HTML**, **CSS**, et **JavaScript**.
- **Backend** : Traitement des fichiers `.vcf` et logique d'analyse/modification des numéros.
- **Bibliothèques utilisées** :
  - [vCard Parser](https://www.npmjs.com/package/vcf-parser) pour lire et écrire des fichiers `.vcf`.

---

## Instructions d'Utilisation

### Étape 1 : Importer un Fichier `.vcf`
1. Cliquez sur le bouton **Importer un fichier** et sélectionnez un fichier `.vcf`.
2. L'application analysera les contacts pour identifier les numéros nécessitant une modification ou un ajout.

### Étape 2 : Visualiser les Modifications
1. Cliquez sur **Afficher les modifications proposées** pour voir :
   - Les numéros à mettre à jour.
   - Les numéros secondaires à ajouter.
2. Examinez les résultats affichés :
   - Nom du contact.
   - Ancien numéro.
   - Nouveau numéro (ou numéro secondaire).

### Étape 3 : Valider et Télécharger
1. **Pour mettre à jour les contacts** :
   - Cliquez sur **Valider les modifications** pour confirmer les changements.
   - Téléchargez le fichier `.vcf` mis à jour.

2. **Pour créer des numéros secondaires** :
   - Cliquez sur **Créer un numéro secondaire**.
   - Téléchargez le fichier `.vcf` contenant les numéros secondaires.

---

## Captures d'Écran

### Interface Principale
![Interface Principale](screenshot-main.png)

### Aperçu des Modifications
![Aperçu des Modifications](screenshot-preview.png)

---