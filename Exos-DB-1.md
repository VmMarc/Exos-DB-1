# Exercices database partie 1

# 1

Créer une base de donnée "db_1" qui contient une table "users" qui correspond à la database que nous avons créé dans le cours précédent sur express:

```js
const users = {
  alice: '123',
  bob: '456',
  charlie: '789',
}
```

Créez les bons champs et donner les bons types à chaque champs. N'oubliez pas un champ "id" qui correspondra à la clé primaire.  
Ensuite afficher toutes les lignes de la table "users" de la base de donnée "db_1".  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
CREATE TABLE users (id SERIAL PRIMARY KEY, name VARCHAR(30), password VARCHAR(30));
```
```sql
INSERT INTO users (name, password) VALUES ('alice', 123), ('bob', 456), ('charlie', 789);
```
```sql
SELECT * FROM users;
```

# 2

Ajouter 3 utilisateurs 'dan', 'eve', 'faythe' qui auront respectivement les password '101112', '131415', '161718'.  
Affichez toutes les lignes de la table "users" de la base de donnée "db_1".  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
INSERT INTO users (name, password) VALUES ('dan', 101112), ('eve', 131415), ('faythe', 161718);
```

# 3

Affichez toutes les lignes de la table "users" de la base de donnée "db_1" dont le password possède plus de 3 caractères. Pour cela il vous faudra utiliser la fonction `LENGTH`.  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
SELECT * FROM users WHERE LENGTH(users.password) > 3;
```

# 4

Modifiez la table "users" afin d'ajouter une nouvelle colonne "bio" qui contiendra une description a propos de l'utilisateur. Ce champ "bio" sera du texte avec un nombre de caractères illimités et sa valeur par défaut sera "Hello, world!".  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
ALTER TABLE users ADD COLUMN bio TEXT DEFAULT 'Hello, world!';
```

# 5

Modifiez toutes les lignes existantes pour que la "bio" de chacun affiche, "Hello, i am PRENOM_DU_USER".  
Il faudra remplacer `PRENOM_DU_USER` par le véritable login de l'utilisateur.  
Il faudra pour cela utiliser la fonction `FORMAT`.  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse:

```sql
UPDATE users SET bio = FORMAT('Hello, I am %s', name);
```

# 6

Afficher les 2 lignes qui ont les "id" les plus grands par ordre décroissant.  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
SELECT * FROM users ORDER BY id DESC LIMIT 2;
```

# 7

Afficher toutes les lignes de la table "users" dont les "id" sont impairs par ordre croissant.  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
SELECT * FROM users WHERE MOD(id, 2) = 1 ORDER BY id ASC;
```

# 8

Effacez toutes les lignes de la table "users" dont les "id" sont pairs.
Affichez toutes les lignes de la table users.  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
DELETE FROM users WHERE MOD(id, 2) = 0;
```
```sql
SELECT * FROM users;
```

# 9

Effacer la TABLE "users".  
Effacer la DATABASE "db_1".  
Vous devrez fournir les commandes SQL entrées ainsi que tous les outputs de ces commandes.

Reponse: 

```sql
DROP TABLE users;
```

```sql
DROP DATABASE db_1;
```
