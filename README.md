# AutoLoc

Projet du module Architecture des SI (4CCE). C'est une api de location de voitures faite avec Spring Boot, on la construit petit a petit a chaque atelier.

## Atelier 1 : projet Spring Boot + premiere entité

Pour cet atelier j'ai crée le projet autoloc-api avec Spring Initializr (Maven, Java 17, groupe tn.esprit.autoloc). Les dependances utilisées sont Spring Web, Spring Data JPA, MySQL Driver, Lombok, Validation et DevTools.

La base c'est MySQL, elle s'appelle autoloc_db et elle est crée automatiquement au demarrage grace a createDatabaseIfNotExist=true dans l'url. Hibernate est en ddl-auto=update donc les tables sont générées a partir des entités, pas besoin d'ecrire le SQL a la main.

Le mot de passe de la base n'est pas dans le fichier application.properties, il faut le mettre dans une variable d'environement avant de lancer :

    DB_PASSWORD=ton_mot_de_passe

(DB_USERNAME est optionel, par defaut c'est root)

J'ai aussi preparé les packages pour la suite : domain, repository, service, web.controller et web.dto. Pour l'instant il y a que domain qui est remplis.

La premiere entité c'est Vehicule avec immatriculation, marque, modele, categorie, tarifJournalier et statut. Categorie et statut sont des enums (CategorieVehicule et StatutVehicule) stockés en texte dans la base. J'ai utilisé Lombok avec @Getter et @Setter et pas @Data parceque ca pose probleme avec les relations bidirectionelles qu'on va faire a l'atelier 2.

## Travail a la maison (prepa atelier 2)

J'ai ajouté les autres entités sur le meme modele que Vehicule, sans les associations pour le moment : Agence, Client, Employe, Equipement, Reservation, Contrat, Paiement et Maintenance. Il y a aussi trois nouveaux enums, RoleEmploye, StatutReservation et ModePaiement.

Ca fait 9 tables au total quand on lance l'application.

## Lancer le projet

Il faut avoir MySQL qui tourne sur le port 3306, ensuite dans le dossier autoloc-api :

    ./mvnw spring-boot:run

Dans les logs on doit voir les "create table" puis "Started AutolocApiApplication".
