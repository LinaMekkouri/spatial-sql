# TD-3: Fonctions de SQL Spatial
## Étape 1 : Importer le shapefile dans PostGIS

1. **Téléchargez le shapefile** des parcelles de Floride :
   [Lien vers le shapefile](https://maps.leegov.com/datasets/80708a2f5f56426f94c8be97c182176b/about).

2. **Importer le shapefile** dans une table PostgreSQL :
   - Ouvrez **PostGIS Shapefile Import/Export Manager** (tapez "shap" dans la recherche Windows pour accéder à l'outil).
   - Sélectionnez le fichier shapefile.
   - Importez les données dans une table PostgreSQL appelée `parcels`.

3. **Vérifiez le contenu de la table** dans **pgAdmin** :
   ```sql
   SELECT COUNT(*) FROM parcels;
## Étape 2 : Identifier le point d'incendie

1. Sélectionnez le centroïde de la parcelle `462273` comme point d'incendie :
   ```sql
   SELECT ST_Centroid(geom) AS fire_point
   FROM parcels
   WHERE gid = 462273;
## Étape 3 : Zone de risque à 1 km

1. **Créer une couche QGIS nommée `fire-risk`** :
   - Dupliquez la couche `parcels`.
   - Cliquez droit sur la couche dupliquée, puis sélectionnez **Filtrer**.

2. **Appliquer un filtre pour les parcelles dans un rayon de 1 km** :
   - Utilisez l'expression suivante dans la zone « Expression de filtrage » :
     ```sql
     ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000)
     ```

3. **Changer la symbologie** pour représenter visuellement les zones à risque.
4. **Ajouter un deuxième point d'incendie (parcelle `460957`)** :
   - Modifiez le filtre pour inclure les deux points d'incendie :
     ```sql
     ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 462273), 1000)
     OR
     ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM "public"."parcels" WHERE gid = 460957), 1000)
## Étape 4 : Répondre aux questions spatiales

1. **Combien de parcelles se trouvent dans un rayon de 1 km autour des deux points d'incendie ?**
   ```sql
   SELECT COUNT(*)
   FROM parcels
   WHERE ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 462273), 1000)
   OR ST_DWithin(geom, (SELECT ST_Centroid(geom) FROM parcels WHERE gid = 460957), 1000);

## Résultats attendus

1. Vous avez identifié les parcelles situées dans un rayon de 1 km autour de points d'incendie.
2. Vous avez calculé la superficie totale des parcelles proches des foyers d'incendie.
3. Vous avez visualisé les zones à risque dans **QGIS** avec une symbologie spécifique.
