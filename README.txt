### ANALYSE DE VENTES DE VIDEOS 


### A propose 

Jeu de données ectracter depuis https://www.vgchartz.com
 utiliser pour l'analyse :
  --Jeux le plus populaire dans différentes Régions 
  --Jeux le plus populaire à travers différents consoles/regions/genre



### Transformation 

Utilisation de Juter notebook [Jupyter notebook] (data_transforme.ipynb) pour le nettoyages et transfromation 
des données :
   -- Supressions de valeurs qui n'ont pas eu de ventes 
   -- Suppresuins des colonnes indésirable 
   -- Convertions des types données 
   -- Chargement de fichier tranformé dans  [CSV file](datasets/jeu_videos_data.csv) et ce sera utilisé pour 
la modelisation


### Modelisation 

Etape pour transformer le données en miltiples dataframe pour l'analyse :
 -- [ERD](modelisatio_donnees/ERD.png)
 --[SQL script](ingenierrie_données/sql_schema.pdf)


### Analyse de données 

[analysis](analyse_donnees/Analyse_SQL.pdf) : 
1. SQL query pour determiner l'annees ou North America on eu plus de ventes.
2. SQL query pour determiner l'annees ou global sales a obtenu plus de ventes.
3. SQL query pour determiner l'annees the total ou on expédiées plus de jeux.
3. SQL query pour determiner le plus populaire de jeux vidéos par console en North America.
4. SQL query pour determiner le plus populaire de jeux vidéos par console en PAL.
5. SQL query pour determiner le plus populaire de jeux vidéos par console en Japan.
6. SQL query pour determiner le plus populaire de jeux vidéos par console en Other regions.
7. SQL query pour determiner le plus populaire de jeux vidéos par console en global.
8. SQL query pour determiner le plus populaire de jeux vidéos expédiées par console.
9. SQL query pour determiner le plus populaire de jeux vidéos à travers différents consoles.
10. SQL query pour determiner le plus populaire de jeux vidéos à travers différents genres.


### Languanges de programmations et application utilisés : 
***
-   Python
    *   Numpy
    *   OS
    *   Pandas
    *   Dbeaver (SQL)
    *   Power Bi (Dashboard)
-   Jupyter Notebook


