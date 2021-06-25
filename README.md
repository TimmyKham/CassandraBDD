# CassandraBDD

### Apache Cassandra est un système de base de données distribuée très puissant, et particulièrement efficace pour prendre en charge de larges volumes d’enregistrements répartis sur de multiples serveurs. Ci-dessous ce trouve un projet avec 3 nodes
----------------------------
:warning: **Il fortement recommandé de tester le projet sous un environnement MAC ou LINUX et de supprimé le contenu du dossier /Data**


## Démarrer et tester le cluster

Démarer le projets

```console
docker-compose up -d
```
Vérifiez que les conteneurs Cassandra démarrent

```console
docker ps
```
Surveiller l'état du cluster


```console
docker exec cass1  nodetool status
```
Vérifiez que CQL fonctionne

```console
docker exec -it cass1   cqlsh  -e "describe keyspaces"
```

Toutes nos félicitations! Vous avez un cluster fonctionnel !


## Ci-dessous quelques requêtes :
Création d'un keyspace
```console
CREATE KEYSPACE tuto WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 3};
```
Accéder à la keyspace
```console
use tuto;
```
Création de la table
```console
CREATE TABLE emp( emp_id int PRIMARY KEY, emp_name text, emp_city text, emp_sal varint, emp_phone varint );
```
Insertion de valeur dans la table
```console
INSERT INTO emp (emp_id, emp_name, emp_city,
   emp_phone, emp_sal) VALUES(1,'ram', 'Hyderabad', 9848022338, 50000);
```
