# spatial-sql
# TD-1 : Installation de PostGIS et Création d’une Base de Données Spatiale

Ce document décrit les étapes pour installer PostgreSQL et PostGIS, et pour créer une base de données spatiale en utilisant pgAdmin.

## 1. Installation de PostgreSQL

### Étapes :
1. Téléchargez la dernière version de PostgreSQL adaptée à votre système d'exploitation depuis [PostgreSQL Downloads](https://www.postgresql.org/download/).
2. Suivez le guide d'installation pour Windows, Linux, ou MacOS.
3. Pendant l'installation :
   - Définissez un mot de passe pour l'utilisateur `postgres`. **Conservez ce mot de passe**, il sera nécessaire pour se connecter à PostGIS.

---

## 2. Installation de PostGIS

### Étapes :
1. Pendant l'installation de PostgreSQL, assurez-vous de cocher **tous les composants** nécessaires.
2. Lancez **Stack Builder** lorsque l'installation vous le propose.
3. Sélectionnez la version de PostgreSQL installée, puis choisissez **PostGIS** dans la liste des extensions disponibles.
4. Suivez les étapes pour installer PostGIS :
   - Spécifiez un dossier d'installation.
   - Confirmez que l'installation est réussie.
5. Une fois terminé, PostGIS sera installé comme extension de votre PostgreSQL.

---

## 3. Création d’une Base de Données Spatiale avec pgAdmin

### Étapes :
1. Ouvrez **pgAdmin**.
2. Connectez-vous en entrant le mot de passe défini lors de l'installation de PostgreSQL.
3. Créez une nouvelle base de données :
   - Clic droit sur **PostgreSQL** > **Create** > **Database**.
   - Entrez un nom pour votre base de données (par exemple : `spatial-db-1`), puis cliquez sur **Save**.

4. Ajoutez l'extension PostGIS à la base de données :
   - Accédez à votre base de données dans **Databases**.
   - Faites un clic droit, puis sélectionnez **Query Tool**.
   - Exécutez la commande SQL suivante :
     ```sql
     CREATE EXTENSION postgis;
     ```
   - Cliquez sur le bouton **Exécuter** ou appuyez sur `F5`.

5. Vérifiez que l'extension a été ajoutée :
   - Développez les éléments suivants : **Schemas** > **Public** > **Tables**.
   - Vous devriez voir une table appelée `spatial_ref_sys`. Cela confirme que l'extension PostGIS est active.

---

## Résultat Final

Vous avez maintenant installé PostgreSQL, ajouté PostGIS, et configuré une base de données spatiale prête à l'emploi !

## Références

- [Documentation officielle de PostgreSQL](https://www.postgresql.org/docs/)
- [Documentation officielle de PostGIS](https://postgis.net/documentation/)
