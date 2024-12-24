# TD-2 : Création de tables avec colonnes spatiales
## Étape 1 : Créer une table spatiale (points)

### Instructions
1. **Créer une table `points_of_interests`** avec une colonne géométrique de type Point :
   ```sql
   CREATE TABLE points_of_interests (
       id SERIAL PRIMARY KEY,
       nom VARCHAR(255),
       geom GEOMETRY(Point, 4326)
   );
## Étape 2 : Créer une table spatiale (polygones)

### Instructions
1. Créer une table `zones_protegees` avec une colonne géométrique de type Polygon :
   ```sql
   CREATE TABLE zones_protegees (
       id SERIAL PRIMARY KEY,
       nom VARCHAR(255),
       geom GEOMETRY(Polygon, 4326)
   );

## Étape 3 : Créer une table spatiale (linestrings)

### Instructions
1. Créer une table `chemins` avec une colonne géométrique de type LineString :
   ```sql
   CREATE TABLE chemins (
       id SERIAL PRIMARY KEY,
       nom VARCHAR(255),
       geom GEOMETRY(LineString, 4326)
   );

## Résultats attendus
À la fin de ce TD, vous aurez créé et manipulé les tables suivantes :
1. Une table `points_of_interests` contenant des points.
2. Une table `zones_protegees` contenant des polygones.
3. Une table `chemins` contenant des lignes (LineString).

## Remarques
- PostGIS doit être activé dans votre base de données PostgreSQL.
- Les données géométriques doivent respecter la projection EPSG:4326.
