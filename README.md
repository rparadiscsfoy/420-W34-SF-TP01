# TP1 - Réservation de billet d'avions

## 1 - Directives

### 1.1 - Déroulement du TP

- Remise du travail: 6 décembre 2022, 23:59
- Ce travail est réalisé en équipe de 2 personnes et seuls les membres de cette équipe y contribuent
- Toutes les réponses fournies doivent être originales (produites par l’étudiant ou un membre de l’équipe)
- Toute copie de code, de portion de code, d’algorithme ou de texte doit faire mention de sa source
- L’emprunt ou la copie de code ou de portions de code est interdite
- Tout constat de plagiat, tricherie ou fraude sera automatiquement déclaré à la Direction et les sanctions prévues seront appliquées
- Vous devez utiliser votre dépôt Git pour faire votre travail : si une situation particulière est détectée, vos commits moduleront votre note dans le groupe et peut même aller jusqu'à un zéro en cas de non participation. (Attention à l'utilisation de 4 mains sur un compte Git !)
- Durée : 3 x 3 heures + travail à la maison
- Plate forme : Azure DevOps et dotnet/react

### 1.2 - À remettre sur la plateforme d'enseignement Léa

- Votre code source SQL dans le répertoire src/SQL sur Git
- Le contenu de ce répertoire zippé sur Léa avant la date indiquée

En résumé, vous pouvez simplement archiver le contenu de votre dépôt Git qui devrait contenir tous ces éléments au moment de la remise.

## 2 - Contexte

Vous devez créer une première version d'une base de données permettant de modéliser des voyages en avions. Un voyage peut être composé d'un ou plusieurs billets. Un billet est associé à une occurrence de vol.

Voici l'ERD qui vous a été fourni par votre analyste :

![ERD logique](images/ERD/airline_reservation/erd_airline_reservation_logique.svg)

Votre analyste vous a indiqué que deux informations ne sont pas forcément renseignées :

- il n'y a pas de numéro de passport pour les vols intérieurs
- la date d'autorisation parentale est seulement requise pour les mineurs

## 3 - À réaliser

- Modifier le fichier AUTHORS.md
- Ajouter les clefs primaires / étrangères
- Justifier, en commentaires, le type de clefs que vous avez choisi
- Ajouter des index où cela est approprié
- Déduire les types de données
- Script SQL permettant d'implanter l'ERD
- Créer des données de test
- Écrire les requêtes suivantes :
  - Afficher l'ensemble des vols disponibles pour chaque compagnie aérienne
  - Afficher l'ensemble des vols qui n'ont pas eu d'occurrence depuis plus de 60 jours
  - Afficher le nombre de voyageurs pour un vol
  - Afficher les étapes d'un voyage pour un client
  - Afficher les étapes de voyage pour un client avec une numérotation des étapes dans l'ordre et l'addition des durées estimées à la fin de l'étape courante
  - Afficher le voyage le plus long pour le mois courant
  - Afficher la liste des voyages pour la journée courante
  - Afficher le nombre de voyages pour la journée courante
  - Afficher les voyages non terminés
  - Afficher le nombre de voyageurs ayant un et un seul voyage intérieur (Donc une étape) pour une date précise (année, mois et jour)
  - Afficher les pays par ordre descendant du nombre d'aéroports

## 4 - Contraintes

- N'oubliez pas de respecter les nomenclatures demandées en cours
- Optimisez vos requêtes
- Partage entre équipier de code avec Git
- Remise finale sur Léa

Tout partage de code, d'explication, de bouts de texte, etc. est considéré comme du plagiat. Pour plus de détails, consultez le site (et ses vidéos) [Sois intègre du Cégep de Sainte-Foy](http://csfoy.ca/soisintegre) ainsi que [l'article 6.1.12 de la PÉA](https://www.csfoy.ca/fileadmin/documents/notre_cegep/politiques_et_reglements/5.9_PolitiqueEvaluationApprentissages_2019.pdf)

## Contributions

- Liste des aéroports : extrait de https://portail-portal.otc-cta.gc.ca/fr/liste-aeroports-internationaux avec JS :

```JS
a.filter(aa => aa.active).map(aa => { return {iata: aa.iata, nom: aa.nameFr, latitude: aa.latitude,longitude:aa.longitude, ville:aa.city.nameFr, pays:aa.city.country.nameFr };}).map(aa => [aa.iata, aa.nom, aa.latitude, aa.longitude, aa.ville, aa.pays].join(";")).join("\n")
```

- Liste pays : extrait de https://fr.wikipedia.org/wiki/ISO_3166-1

Ces listes sont disponibles dans le fichier excel liste_aeroports_pays.xls