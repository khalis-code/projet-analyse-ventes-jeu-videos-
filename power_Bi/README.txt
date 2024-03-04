# Data Analysis Expressions - Les Formules DAX

Légende
- Colonne Calculée (ColCal)
- Mesure (Mes)
- Table Calculée (TabCal)
- Chiffe d'affaire (Total sales)

## Définitions

Une `formule` est une ou plusieurs expressions DAX servant à définir un calcul de modèle. 

Les `formules DAX` sont des collections de functions, d'opérateurs et de constantes qui vous 
permettent de créer des `colonnes calculées`, des `mesures` et des `tables calculées` à partir 
des données présent dans un modèle de données afin de résoudre des problèmes concrets dans votre entreprise. 
Les formules DAX sont utilisés dans `Power Pivot` (Excel), dans `Power BI` (Desktop et Service), 
dans `Azure Analysis Services` et lors de la modélisation tabulaire dans `SQL Server Analysis Services`. 

Une `colonne calculée` est un calcul de modèle qui vise à ajouter une colonne à un modèle tabulaire 
en écrivant une formule DAX qui évalue séquentiellement chaque ligne de la table et retourne une valeur 
scalaire (valeur unique) correspondante.

Une `mesure` par contre, est un calcul de modèle qui aggrège par défaut, toutes les lignes d'une table 
pour générer une valeur scalaire. Power BI Desktop recalcule cette valeur scalaire toute fois que la mesure 
est introduite dans un visuel contenant des champs (filtres contextuels). Vous pouvez aussi modifier cette 
valeur scalaire manuellement en utilisant les fonction de filtre ALL, RELATED, FILTER et CALCULATE.

Une `table calculée` est un calcul de modèle qui vise à ajouter une table à un modèle tabulaire en écrivant 
une formule DAX qui, contraire à celle d'une colonne calculée, retourne plutôt une table.

Un `calcul de modèle` est une formule nommée servant à ajouter une table calculée, une colonne calculée ou 
une mesure à un modèle de données tabulaire. Sa structure est [NOM] = [FORMULE]. 


Un `contexte` décrit l’environnement dans lequel une formule DAX est évaluée. Il existe deux types de 
contexte : le contexte de ligne et le contexte de filtre. Dans un contexte de ligne, la formule DAX est 
évaluée lors de la création de la colonne calculée ou lors de l'utilisation du formule itération (formule-X) 
pour chaque ligne de la table du modèle. Dans un contexte de filter créer par un ou plusieurs champs de modèle 
ajoutés à un visuel, une ou plusieurs fonctions de filtre ajoutés une formule, la formule DAX initiale est 
évaluée pour chaque filtre ou chaque combinaison de filtres présents.

## Les colonnes calculées

### Examples illustratifs 
 -- SQL query pour determiner l'annees ou North America on eu plus de ventes.
EVALUATE
SUMMARIZE(
    FILTER(
        INNERJOIN(
            sales,
            games,
            games[game_id] = sales[game_id]
        ),
        NOT ISBLANK(sales[na_sales_in_millions])
    ),
    games[release_YEAR],
    "total_na_sales", SUM(sales[na_sales_in_millions])
)
ORDER BY [total_na_sales] DESC
LIMIT 1


-- SQL query pour determiner le plus populaire de jeux vidéos à travers différents global sales

EVALUATE
SUMMARIZE(
    FILTER(
        INNERJOIN(
            INNERJOIN(
                INNERJOIN(
                    games,
                    console,
                    games[console_id] = console[console_id]
                ),
                sales,
                games[game_id] = sales[game_id]
            ),
            (
                SELECTCOLUMNS(
                    SUMMARIZE(
                        games,
                        console[console_id],
                        "max_global_sales_in_millions", MAX(sales[global_sales_in_millions])
                    ),
                    "console_id", [console_id],
                    "max_global_sales_in_millions", [max_global_sales_in_millions]
                )
            ),
            games[console_id] = [console_id]
        ),
        sales[global_sales_in_millions] = [max_global_sales_in_millions]
    ),
    games[game_name],
    console[console]
)
ORDER BY console[console_id]




