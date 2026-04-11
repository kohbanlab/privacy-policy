EN:
# CheckHome Privacy Policy

Last updated: April 11, 2026

Official published URL: https://kohbanlab.github.io/privacy-policy/checkhome

## 1. Scope

This policy applies to the Android application `CheckHome`.

CheckHome is used to prepare and export property inspection reports. Based on the code currently present in the application, the app primarily stores inspection data locally on the device and only sends limited data to external services when a specific feature requires it.

## 2. Data processed by the app

The app can process the following categories of data:

- Property and inspection data: property address, inspection date, lease details, meter readings, access items, room status, comments, observations.
- Contact data entered by the user: owner names, tenant names, phone numbers, email addresses, postal addresses.
- Media created in the app: room photos, accessory photos, handwritten signatures, certified handwriting images, temporary export files.
- Local preference data: expert name and the last inspection resumed, stored in Android DataStore.

## 3. Why the data is used

The app uses this data to:

- create and update a property inspection file;
- generate a final PDF inspection report;
- reopen the last in-progress inspection;
- attach photos and signatures to the report;
- help the user search for and normalize a French postal address.

## 4. Local storage

Based on the audited code:

- inspection records are stored in a local Room database;
- photos, signatures, certified handwriting images and temporary export files are stored in the app's private internal storage;
- minimal preferences are stored in Android DataStore;
- Android automatic backup is disabled in the manifest.

## 5. External data flows

The audit confirmed the following external flows:

- Address autocomplete: the text typed into the address search field is sent to the French public address API at `https://api-adresse.data.gouv.fr/search/` to return suggestions.
- PDF export to device storage: when the user exports a report, the app copies the final PDF to the device download area, in `Downloads/CheckHome`.
- PDF sharing: when the user taps the share action, the PDF is intentionally shared with another application chosen by the user.

The audit did not find a backend service in CheckHome that uploads full inspection files to a developer-managed server.

## 6. PDF export and file names

PDF file names have been sanitized to avoid exposing names, addresses, email addresses or phone numbers in file names.

The app now uses:

- `checkhome_YYYYMMDD_HHMMSS.pdf` for the public exported PDF;
- `inspection_<uuid>.pdf` for the internal temporary export file.

## 7. Deletion

The current app code now deletes, when an inspection is removed from the app:

- the related Room database records;
- internal inspection folders;
- room photos and accessory photos;
- signature and certified handwriting files;
- residual voice-note files referenced by the data model;
- known exported PDF files created by the app on the same device, when their location is still tracked by the app.

Important limitation:

- if the user already shared the PDF to a third-party service or copied it outside the app's control, CheckHome cannot delete that remote copy;
- if a PDF was manually moved or renamed outside the app after export, deletion may no longer be possible from the app.

## 8. Security measures

Based on the audited code:

- the app uses app-private internal storage for working files;
- Android automatic backup is disabled (`android:allowBackup="false"`);
- PDFs are shared through Android's permissioned content sharing mechanisms;
- unnecessary `RECORD_AUDIO` permission was removed.

## 9. GDPR / privacy rights

Depending on your jurisdiction, you may have rights to access, correct, delete or limit the processing of your data.

In practice for this app:

- you can edit inspection data directly in the app;
- you can delete local inspection files from the app;
- you can delete exported PDFs from the device if they remain under the app's control;
- for support or formal privacy requests, use the contact channel published with the app's Google Play listing and privacy website.

## 10. Children

CheckHome is not designed for children and is not intentionally targeted at children.

## 11. Changes

This policy may be updated when the app's features, storage model or external services change. The current version should be kept aligned with the code actually shipped on Google Play.

FR:
# Politique de confidentialité CheckHome

Dernière mise à jour : 11 avril 2026

URL officielle publiée : https://kohbanlab.github.io/privacy-policy/checkhome

## 1. Périmètre

Cette politique s'applique à l'application Android `CheckHome`.

CheckHome permet de préparer et d'exporter des états des lieux. D'après le code réellement audité, l'application stocke principalement les données en local sur l'appareil et n'envoie des données vers l'extérieur que lorsqu'une fonctionnalité précise en a besoin.

## 2. Données traitées

L'application peut traiter les catégories de données suivantes :

- Données du bien et du dossier : adresse du logement, date d'état des lieux, informations de bail, relevés de compteurs, accès, statut des pièces, commentaires, observations.
- Coordonnées saisies par l'utilisateur : noms des bailleurs, noms des locataires, numéros de téléphone, adresses e-mail, adresses postales.
- Médias créés dans l'application : photos, signatures manuscrites, mentions manuscrites certifiées, fichiers temporaires d'export.
- Préférences locales : nom de l'expert et dernier dossier repris, stockés dans Android DataStore.

## 3. Finalités

Ces données sont utilisées pour :

- créer et mettre à jour un dossier d'état des lieux ;
- produire le PDF final ;
- reprendre le dernier dossier en cours ;
- rattacher des photos et signatures au rapport ;
- aider l'utilisateur à rechercher et normaliser une adresse postale française.

## 4. Stockage local

D'après le code audité :

- les données métier sont stockées dans une base locale Room ;
- les photos, signatures, mentions certifiées manuscrites et exports temporaires sont stockés dans l'espace interne privé de l'application ;
- les préférences minimales sont stockées dans Android DataStore ;
- le backup Android automatique est désactivé dans le manifest.

## 5. Flux externes

L'audit a confirmé les flux sortants suivants :

- Autocomplétion d'adresse : le texte saisi dans le champ de recherche d'adresse est envoyé à l'API publique française `https://api-adresse.data.gouv.fr/search/` pour obtenir des suggestions.
- Export PDF vers l'appareil : lorsqu'un rapport est exporté, l'application copie le PDF final dans la zone de téléchargement du téléphone, sous `Downloads/CheckHome`.
- Partage PDF : lorsqu'un utilisateur choisit l'action de partage, le PDF est transmis à une autre application choisie par l'utilisateur.

L'audit n'a pas trouvé de backend CheckHome envoyant l'intégralité des dossiers vers un serveur géré par l'éditeur.

## 6. Export PDF et noms de fichiers

Les noms de fichiers PDF ont été neutralisés afin de ne plus exposer de noms, d'adresses, d'e-mails ou de numéros de téléphone.

L'application utilise désormais :

- `checkhome_YYYYMMDD_HHMMSS.pdf` pour le PDF exporté publiquement ;
- `inspection_<uuid>.pdf` pour le fichier temporaire interne.

## 7. Suppression

Le code actuel efface maintenant, lorsqu'un dossier est supprimé :

- les lignes Room associées ;
- les dossiers internes du dossier concerné ;
- les photos de pièces et d'accessoires ;
- les signatures et fichiers de mentions certifiées ;
- les fichiers résiduels liés aux notes vocales présents dans le modèle ;
- les PDF exportés connus par l'application sur ce même appareil, tant que leur emplacement reste suivi par l'application.

Limites importantes :

- si le PDF a déjà été partagé vers un service tiers ou copié hors du contrôle de l'application, CheckHome ne peut pas supprimer cette copie distante ;
- si un PDF a été déplacé ou renommé manuellement hors de l'application, sa suppression automatique peut ne plus être possible.

## 8. Sécurité

D'après le code audité :

- l'application utilise l'espace interne privé Android pour les fichiers de travail ;
- le backup Android automatique est désactivé (`android:allowBackup="false"`) ;
- le partage de PDF passe par les mécanismes Android de partage de contenu avec permissions ;
- la permission inutile `RECORD_AUDIO` a été supprimée.

## 9. Droits RGPD et demandes

Selon votre juridiction, vous pouvez disposer de droits d'accès, de rectification, d'effacement ou de limitation.

Concrètement dans l'application :

- vous pouvez modifier les données du dossier directement dans l'application ;
- vous pouvez supprimer les dossiers locaux depuis l'application ;
- vous pouvez supprimer les PDF exportés du téléphone tant qu'ils restent sous le contrôle de l'application ;
- pour une demande formelle relative à la confidentialité, utilisez le canal de contact publié dans la fiche Google Play et sur le site de politique de confidentialité.

## 10. Enfants

CheckHome n'est pas conçu pour les enfants et ne leur est pas destiné.

## 11. Mises à jour

Cette politique doit être mise à jour dès qu'une fonctionnalité, un mode de stockage ou un service externe évolue. La version publiée doit rester alignée avec le code réellement distribué sur Google Play.


