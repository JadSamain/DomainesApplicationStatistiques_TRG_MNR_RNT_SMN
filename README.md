# On retire la coupe de france parce qu'en coupe de france, on peut jouer contre des équipes du niveau inférieure

# DomainesApplicationStatistiques_TRG_MNR_RNT_SMN

TRUONG David / MEUNIER Aubin / RENAULT Thibault / SAMAIN Jad

## Schéma de donnée

![1746781257426](image/README/1746781257426.png)

## Données

- Saison : L'année ou la saison sportive à laquelle les données se réfèrent (par exemple, saison 2024-2025).
- Num_match : Le numéro ou l'identifiant du match dans la saison.
- Competition : Le nom de la compétition ou du tournoi dans lequel le match a eu lieu (ex : Ligue 1, EuroLeague).
- dom_ext : Indique si le match a eu lieu à domicile ("dom") ou à l'extérieur ("ext").
- Gagne_perdu : Résultat du match pour l’équipe (gagné ou perdu).
- Adversaire : Nom de l’équipe adverse.
- Capitaine : Indique si le joueur était le capitaine de l’équipe pendant le match.
- Starter/bench : Statut du joueur dans l'équipe, s’il a commencé le match (starter) ou s’il est resté sur le banc (bench).
- Joueur : Nom ou identifiant du joueur qui a participé au match.
- Minutes : Le nombre de minutes durant lesquelles le joueur a joué.
- Secondes : Le nombre de secondes durant lesquelles le joueur a joué (détail plus précis que les minutes).
- Secondes(minutes) : Conversion des secondes en minutes, généralement pour faciliter les calculs.
- Tps_jeu_decimal : Temps de jeu en format décimal (par exemple, 30 minutes 45 secondes seraient converties en 30.75 minutes).
- Tirs_marques : Le nombre de tirs réussis par le joueur.
- Tirs_tentes : Le nombre total de tirs tentés par le joueur.
- %Tirs : Pourcentage de réussite des tirs, calculé comme (Tirs_marques / Tirs_tentes) * 100.
- 2pts_marques : Le nombre de tirs à deux points réussis par le joueur.
- 2pts_tentes : Le nombre total de tirs à deux points tentés par le joueur.
- %2pts : Le pourcentage de réussite des tirs à deux points, calculé comme (2pts_marques / 2pts_tentes) * 100.
- 3pts_marques : Le nombre de tirs à trois points réussis par le joueur.
- 3pts_tentes : Le nombre total de tirs à trois points tentés par le joueur.
- %3pts : Le pourcentage de réussite des tirs à trois points, calculé comme (3pts_marques / 3pts_tentes) * 100.
- LF_marques : Le nombre de lancers francs réussis par le joueur.
- LF_tentes : Le nombre total de lancers francs tentés par le joueur.
- %LF : Le pourcentage de réussite des lancers francs, calculé comme (LF_marques / LF_tentes) * 100.
- Pts_apres_balles_perdues : Nombre de points marqués après une perte de balle par l’équipe adverse.
- Points_int : Points marqués après des interceptions.
- Point_2eme_chance : Nombre de points marqués suite à une deuxième chance (souvent après un rebond offensif).
- Points_CA : Points marqués en contre-attaque.
- Points_banc : Points marqués par les joueurs venant du banc.
- Ecart_max : L’écart maximum entre les deux équipes durant le match.
- Serie_max : La plus grande série consécutive de points marqués par l’équipe.
- Pts : Nombre total de points marqués par le joueur.
- RO : Nombre de rebonds offensifs captés par le joueur.
- RD : Nombre de rebonds défensifs captés par le joueur.
- RT : Total des rebonds (offensifs + défensifs) captés par le joueur.
- PD : Nombre de passes décisives réalisées par le joueur.
- BP : Nombre de blocks (contre) réalisés par le joueur.
- INT : Nombre d’interceptions réalisées par le joueur.
  CT : Nombre de fautes commises par le joueur.
  CTS : Nombre de fautes subies par le joueur.
  F : Nombre de fautes personnelles commises par le joueur.
  FPR : Le ratio de fautes personnelles commises par rapport à ses minutes de jeu.
  +/- : L'écart de points de l’équipe lorsque le joueur est sur le terrain, aussi appelé le "plus/moins" (différence entre les points marqués par son équipe et ceux marqués par l'adversaire pendant qu'il joue).
  EVAL : L’évaluation globale du joueur, souvent utilisée comme un indicateur de performance. Elle regroupe plusieurs statistiques de performance (points, rebonds, passes, etc.).
  N° : Le numéro du joueur
  JOUEUR : Le nom ou l’identifiant du joueur (peut être une version alternative ou un code du joueur).

## Problématique

Quel style de jeu est le plus efficace en termes de victoire ?

## Style de jeux

1. Style Offensif :

- %3pts (pourcentage de réussite des tirs à 3 points)
- Points_CA (points sur contre-attaque)
- Tirs_marques (nombre de tirs réussis)
- Points (total des points marqués)

2. Style Défensif :

- Opponent FG% (pourcentage de réussite des tirs de l'adversaire)
- INT (interceptions)
- CT (contres)
- Points_int (points encaissés après balles perdues)

3. Style Équilibré :

- Net Rating (différence entre l'Offensive Rating et le Defensive Rating)
- EVAL (évaluation globale des joueurs)
- Points_banc (points marqués par les joueurs du banc)
- Pts (total des points marqués)

efficency offensive
taux de possession
rating offenssive and defensive

https://basket-infos.com/2015/08/15/statistiques-avancees-le-lexique/
https://viziball.app/glossary/nba/en
https://www.basketball-reference.com/about/ratings.html 

Possession = 0.5 * (...) + BP
Offensive rating = 100 * ( PTS / POSS)
Defensive rating = 100 * (OppPTS / OppPOSS)
NetRating = Offensive rating - Defensive rating 

Graph à réaliser :
✅ 1. Scatter Plot (nuage de points) – LE MEILLEUR CHOIX

    X-axis : Offensive Rating

    Y-axis : Defensive Rating (utiliser une échelle inversée car un DRtg plus bas est meilleur)

    Optionnel : Taille ou couleur des points = Net Rating

📌 Pourquoi ?
Ce graphe te permet de voir en un coup d'œil :

    Les équipes fortes en attaque (droite du graphique)

    Les équipes fortes en défense (haut du graphique, si l’axe Y est inversé)

    Les équipes équilibrées (en haut à droite)

    Les extrêmes ou déséquilibres (ex : très bonne attaque mais défense faible)

👉 Ajout des noms des équipes pour plus de lisibilité.

💡 Résumé visuel :
But	Graphique conseillé	Axes clés
Identifier les styles de jeu
Scatter Plot multivarié	Pace vs 3PAr (taille = AST%)

Comparer la réussite des styles	
Box Plot ou Bar Plot par style	
Style → Net Rating ou Win %