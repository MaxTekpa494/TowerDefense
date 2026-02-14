# Tower Defense - Jeu de Stratégie en Temps Réel
## Description du Projet
**Tower Defense** est un jeu de stratégie en temps réel développé en langage C, mettant en œuvre des concepts avancés de programmation système et graphique. Le joueur doit défendre sa base contre des vagues successives de monstres en plaçant stratégiquement des tours équipées de gemmes élémentaires possédant des propriétés uniques.
Le jeu propose un système de combat basé sur des éléments (Pyro, Hydro, Dendro) qui peuvent interagir entre eux pour créer des réactions élémentaires, ajoutant une dimension tactique importante au gameplay.


### Architecture du Projet
Le projet est structuré de manière modulaire avec une séparation claire des responsabilités :
```
progc-tekpa_tran/
├── src/           # Code source
│   ├── main.c           # Point d'entrée du programme
│   ├── moteur.c         # Boucle principale et logique du jeu
│   ├── graphique.c      # Rendu graphique et interface
│   ├── vague.c          # Gestion des vagues de monstres
│   ├── game.c           # Gestion des tours et projectiles
│   ├── gemmes.c         # Système de gemmes et fusion
│   ├── mana.c           # Gestion de la ressource mana
│   └── terrain.c        # Génération et gestion du terrain
├── include/       # Fichiers d'en-tête (.h)
├── bin/           # Exécutables et fichiers objets
├── doc/           # Documentation (Doxygen et user.md)
├── makefile       # Système de compilation
└── Doxyfile       # Configuration de la documentation
```
## Fonctionnalités Principales
### 1. Système de Gemmes Élémentaires
- **Trois éléments** : Pyro (feu), Hydro (eau), Dendro (nature)
- **Types de gemmes** : Pure (un seul élément) ou Mixte (deux éléments)
- **Système de niveau** : Fusion de gemmes pour augmenter leur puissance
- **Propriétés uniques** : Chaque gemme possède une teinte et des statistiques spécifiques
### 2. Système de Combat
- **Portée d'attaque** : Les tours équipées de gemmes ciblent les monstres à portée
- **Projectiles** : Système de tir avec trajectoires calculées en temps réel
- **Dégâts** : Calcul basé sur le niveau de la gemme, l'élément et la teinte du monstre
- **Dégâts de zone (Splash)** : Certaines attaques affectent plusieurs ennemis
- **Réactions élémentaires** : 
  - Pyro + Hydro = Vaporisation (dégâts bonus)
  - Hydro + Dendro = Enracinement (ralentissement)
  - Pyro + Dendro = Poison (dégâts dans le temps)
### 3. Types de Vagues
Le jeu génère différents types de vagues avec des probabilités variées :
- **Vague Normale (50%)** : Nombre modéré de monstres avec statistiques standard
- **Vague de Foule (20%)** : Nombreux monstres avec HP réduits
- **Vague Agile (20%)** : Monstres rapides mais fragiles
- **Vague Boss (10%)** : Peu de monstres mais très résistants
### 4. Système d'Effets
Les monstres peuvent être affectés par divers effets :
- **Ralentissement (SLOW)** : Réduit la vitesse de déplacement
- **Poison** : Inflige des dégâts continus
- **Vaporisation** : Dégâts élémentaires instantanés
- **Enracinement** : Immobilisation temporaire
### 5. Gestion des Ressources
- **Mana** : Ressource principale pour créer des gemmes et construire des tours
- **Gain de mana** : Obtenu en éliminant des monstres
- **Coût évolutif** : Les actions deviennent plus coûteuses au fil du jeu
## Aspects Techniques Notables
### 1. Algorithmes et Structures de Données
- **Pathfinding** : Génération procédurale de chemins pour les monstres
- **Détection de collision** : Calcul de distance euclidienne pour la portée des tours
- **Gestion de listes dynamiques** : Réorganisation efficace des tableaux de projectiles et monstres
- **États et effets** : Machine à états pour gérer les effets sur les monstres
### 2. Programmation Orientée Événements
- **Boucle de jeu** : Architecture basée sur une boucle principale avec mise à jour à 60 FPS
- **Gestion des entrées** : Clavier (espace, touche 't') et souris (clics gauche/droit)
- **Système de timing** : Utilisation de timestamps pour les animations et cooldowns
### 3. Rendu Graphique
- **Interface utilisateur** : Boutons, indicateurs de ressources, barres de vie
- **Animations** : Déplacement fluide des monstres et projectiles
- **Feedback visuel** : Couleurs pour représenter les éléments et la santé des monstres
- **Grille de jeu** : Système de coordonnées avec cases de 25x25 pixels
### 4. Gestion Mémoire
- **Allocation statique** : Utilisation de tableaux de taille fixe pour optimiser les performances
- **Nettoyage** : Réorganisation des listes pour éviter les fuites mémoire
- **Structures optimisées** : Tailles calculées pour minimiser l'empreinte mémoire
  
## Installation et Compilation
### Prérequis
- **Système d'exploitation** : Linux (testé sur Ubuntu/Debian)
- **GCC** : Compilateur C (version récente avec support C17)
- **MLV Library** : Bibliothèque graphique MLV
  ```bash
  sudo apt-get install libmlv3-dev
  ```
- **Make** : Utilitaire de build
- **Doxygen** (optionnel) : Pour générer la documentation
### Compilation
1. **Cloner le repository**
   ```bash
   git clone https://github.com/MaxTekpa494/TowerDefense.git
   cd TowerDefense/progc-tekpa_tran
   ```
2. **Compiler le projet**
   ```bash
   make
   ```
   Cette commande génère l'exécutable `tower` dans le dossier `bin/`
3. **Nettoyer les fichiers de compilation**
   ```bash
   make clean
   ```
## Utilisation
### Lancer le Jeu
```bash
bin/./tower
```
### Afficher l'Aide
```bash
bin/./tower -h
```
### Générer la Documentation
```bash
doxygen Doxyfile
```
La documentation HTML sera générée dans `doc/html/`. Ouvrir `doc/html/index.html` dans un navigateur.
## Guide du Joueur
### Contrôles
| Action | Commande |
|--------|----------|
| **Déclencher une vague** | Appuyer sur `ESPACE` |
| **Créer une gemme** | Cliquer sur le bouton "Create" (en bas à droite) |
| **Améliorer une gemme** | Cliquer sur le bouton "Upgrade" (en bas à gauche) |
| **Placer une tour** | Appuyer sur `T`, puis cliquer gauche pour valider ou clic droit pour annuler |
| **Équiper une gemme** | Cliquer gauche sur la gemme, puis cliquer gauche sur une tour pour l'équiper |
| **Annuler une action** | Clic droit |
### Stratégies de Base
1. **Économie de mana** : Ne créez pas trop de gemmes au début, concentrez-vous sur les premières tours
2. **Fusion stratégique** : Fusionnez les gemmes pour obtenir des niveaux supérieurs et des dégâts accrus
3. **Positionnement** : Placez les tours aux endroits où les monstres passent le plus de temps
4. **Synergie élémentaire** : Utilisez des tours avec différents éléments pour déclencher des réactions
5. **Préparation** : Construisez votre défense avant de déclencher les vagues

## Auteurs
- **TEKPA Max** - Groupe TP 1
- **TRAN Thien-Loc** - Groupe TP 1
