## Requêtes SQL

### Exercice 1 :
Listez l’ensemble des jeux enregistré dans la table « games ».
SELECT * FROM games;
### Exercice 2 :
Listez l’ensemble de jeux sans les doublons.
SELECT DISTINCT * FROM games;
### Exercice 3 :
Affichez le nom, le mode de jeu, la date de sortie et le pegi de tous les jeux triés par ordre alphabétiques.
SELECT DISTINCT * FROM games ORDER BY g_name ASC;
### Exercice 4 :
Affichez le nom, le mode de jeu, la date de sortie et le pegi des 10 jeux les plus récents.
SELECT DISTINCT g_name, games_genres, g_id, g_pegi FROM `games` ORDER BY `g_published_at` DESC LIMIT 10;

### Exercice 5 :
Affichez le nom et le mode de jeu des jeux qui se jouent uniquement dans un seul mode
SELECT g_name, g_mode FROM `games` WHERE g_mode NOT LIKE '%/%';

### Exercice 6 :
Affichez le nom et la date de sortie des jeux sortie entre 2015 et 2020 triés par année
SELECT g_name, g_published_at FROM games WHERE YEAR(g_published_at) IN (2015, 2016, 2017, 2018, 2019, 2020) ORDER BY g_published_at ASC LIMIT 10;

### Exercice 7 :
Affichez le nom et le mode de jeu des jeux qui peuvent se jouer en mode solo
SELECT g_name, g_mode FROM `games` WHERE g_mode LIKE '%Solo%';

### Exercice 8 :
Affichez les informations des différents jeux "witcher" disponibles.
SELECT * FROM games WHERE g_name LIKE '%Witcher%';

### Exercice 9 :
Affichez les informations de tous les jeux sauf les jeux «Halo".
SELECT * FROM games WHERE g_name NOT LIKE '%Halo%';

### Exercice 10 :
Lister les jeux sortis en 2012, 2016 et 2020.
SELECT g_name, g_published_at FROM games WHERE YEAR(g_published_at) IN (2012, 2016, 2020);

### Exercice 11 :
Affichez le nom de jeu et le studio de tous les jeux. Utiliser une jointure naturelle.
SELECT games.g_name, studios.s_name FROM games INNER JOIN studios ON games.s_id = studios.s_id;

### Exercice 12 :
Affichez le nom de jeu, le studio, la nationalité de la société des jeux disponibles. Utiliser une jointure avec join
SELECT games.g_name, studios.s_name, studios.s_nationality FROM games INNER JOIN studios ON games.s_id = studios.s_id;

### Exercice 13 :
Affichez le nom et le mode de jeu des jeux console grand public triés par pegi croissant
SELECT g_name, g_pegi, g_mode FROM games ORDER BY g_pegi;

### Exercice 14 :
Affichez le nom de jeu et les plateformes de tous les jeux triés par ordre alphabétique
SELECT games.g_name, games_platforms.p_id FROM games
INNER JOIN games_platforms ON games.p_id = games_platforms.p_id;
(J'AI ESSAYE CA MAIS COMMENT CONNAITRE LA PLATFORM DU JEU ? (IL Y A PAS D'ID DE PLATFORM DANS LA TABLE GAME J'AI PAS TROUVE COMMENT FAIRE))

### Exercice 15 :
Calculez le nombre total de jeux.
SELECT COUNT(*) FROM games;

### Exercice 16 :
Affichez le nombre de jeux uniques.
SELECT COUNT(DISTINCT g_name) FROM games;


### Exercice 17 :
Calculez le nombre de jeux par studio.
SELECT studios.s_name, COUNT(games.g_name) AS number_of_games FROM games INNER JOIN studios ON games.s_id = studios.s_id GROUP BY studios.s_name;

### Exercice 18 : 
Calculez le nombre de jeux par studio et par plateforme


### Exercice 19 : 
Affichez les jeux disponibles sur au moins 4 plateformes