#  L'univers du Crime : Où Mystères et Intrigues Se Côtoient - Âmes Sensibles, S'Abstenir!"
![Image Loupe](https://github.com/thizirisaighi/M2_DEFI_SAIGHI_Thziri/blob/main/loupe.jpg?raw=true)
>>> Source: https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQe33j6EuWTfCnvjT-gqyw297x4tqevQ2_5U7i-D-WhjUsWxEcP

   
  
# Sommaire
1. [Introduction](#Intro)
2. [Tueurs en Série](#Série)
3. [Requete SPARQL](#SPARQL)
4. [Crimes dans les régions de France](#Crimes)
5. [Crimes Raciaux  à New York](#NewYork)
6. [Crimes dans le Monde](#Monde)
7. [Tableau des tueurs en série qui ont marqué l'histoire](#Histoire)
8. [Conclusion](#Conclusions)



# Introduction <a name="Intro"></a> 

Bienvenue dans ce projet dédié à l'analyse approfondie et à l'exploration du domaine complexe et fascinant des crimes. À travers cette initiative, notre objectif est de plonger dans les différentes dimensions du comportement criminel, d'identifier les tendances émergentes, et de comprendre les enjeux sociaux associés à ce phénomène.

## Objectifs

Ce projet a pour objectifs principaux : analyser les différentes formes de crimes et leurs manifestations dans la société, examiner les évolutions contemporaines qui influent sur la nature et la prévalence des crimes, comprendre les facteurs sous-jacents qui contribuent au comportement criminel, évaluer les politiques de prévention et les méthodes de justice dans la lutte contre le crime, ainsi que explorer les avancées technologiques et les innovations en matière de lutte contre le crime.

## Définitions

Dans ce contexte, le terme "crime" fait référence à un acte ou une conduite interdite par la loi, entraînant une peine ou une sanction pénale. Les "tendances criminelles" désignent les modèles et évolutions observés dans la fréquence et la nature des crimes au fil du temps. La "prévention du crime" englobe l'ensemble des mesures visant à réduire l'incidence du crime, dissuader les délinquants, et promouvoir la sécurité publique. La "justice pénale" se réfère au système légal et institutionnel chargé de punir les criminels et de réhabiliter les délinquants.
Parailleurs, nous avons voulu plonger dans le monde des tueurs en séries. Un sujet sensible pour lequel la collecte d'informations était très compliquée, mais nous avons tout de même réussi à faire quelques analyses et quelques visualisations.

# Tueurs en Série <a name="Série"></a>   
Les tueurs en série, également connus sous le nom de "serial killers," suscitent fascination et horreur dans l'imaginaire collectif. Ces individus commettent une série de meurtres, souvent avec une méthode distincte, et présentent des caractéristiques psychologiques particulières. Cette présentation explorera la définition, les profils, les motifs et les méthodes associés aux tueurs en série.

## Définition
Un tueur en série est défini comme une personne qui commet au moins trois meurtres distincts sur une période de temps prolongée, avec une période de refroidissement entre chaque crime. Cette définition permet de distinguer les tueurs en série des criminels impulsifs et des tueurs en masse.

## Profilage
Motifs et Caractéristiques
Les tueurs en série présentent souvent des motifs récurrents et des caractéristiques psychologiques distinctes. Certains peuvent être motivés par le plaisir du meurtre, la satisfaction émotionnelle, le pouvoir, la domination, ou même des motifs religieux ou politiques. Leurs profils varient, mais beaucoup partagent des traits tels que la manipulation, la superficialité émotionnelle et la difficulté à établir des relations interpersonnelles.

# Requete SPARQL <a name="SPARQL"></a> 

Nous avons voulu utiliser des reqeuets SPARQL sur WIKIDATA pour  récupérer des données sur notre thème principal qui est les crimes et délits. Cependant, Wikidata ne nous fournit pas les informations nécessaires sur ce sujet. Nous avons néamoins utilisé une requetes Sparql qui  se base sur le service wikibase:label pour obtenir les libellés (labels) de l'entité dans différentes langues 
## Le mot "Crime" dans toutes les langues : 
```sparql
SELECT ?entite ?entiteLabel ?description
WHERE {
  VALUES ?term { wd:Q83267 }
  
  ?term ?predicate ?entite.
  OPTIONAL { ?entite wdt:P1448 ?description. }  # Description de l'entité

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```
## Tueur en Série 
De même que pour "Crime", nous avons eu des difficultés à faire tourner des requetes sur les tueurs en séries. Nous avons tout de meme voulut partager cette " seule requete" SPARQL qui a fonctionné et qui nous offre la définition de " Tueur en Série" dans toutes les langues :
https://w.wiki/8toB        
```sparql
SELECT ?entite ?entiteLabel ?entiteDescription
WHERE {
  VALUES ?term { wd:Q484188 }
  
  ?term ?predicate ?entite.
  OPTIONAL { ?entite schema:description ?entiteDescription. }  # Description de l'entité

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}

SELECT ?entite ?entiteLabel ?entiteDescription
WHERE {
  VALUES ?term { wd:Q484188 }
  
  ?term ?predicate ?entite.
  OPTIONAL { ?entite schema:description ?entiteDescription. }  # Description de l'entité

  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
```



# Crimes dans les régions de France <a name="Crimes"></a> 

Pour cette première visualisation, nous avons voulu présenter les départements de France avec leurs populations,nombre de logements ainsi que l'ensemble des crimes et délits enregistrés par les forces de sécurité en 2016.  
 
<iframe style="width: 80vw; height: 50vh; border: none;" src="https://public.opendatasoft.com/explore/embed/dataset/crimes-et-delits-enregistres-par-les-forces-de-securite-en-2016-par-departement/map/?location=3,51.45401,35.5957&basemap=jawg.light&dataChart=eyJxdWVyaWVzIjpbeyJjaGFydHMiOlt7InR5cGUiOiJjb2x1bW4iLCJmdW5jIjoiQVZHIiwieUF4aXMiOiJ2b2xzX2F2ZWNfYXJtZXNfYXJtZXNfYV9mZXVfYXJtZXNfYmxhbmNoZXNfb3VfcGFyX2Rlc3RpbmF0aW9uIiwic2NpZW50aWZpY0Rpc3BsYXkiOnRydWUsImNvbG9yIjoiIzJDM0Y1NiJ9LHsidHlwZSI6ImNvbHVtbiIsImZ1bmMiOiJBVkciLCJ5QXhpcyI6InZvbHNfdmlvbGVudHNfc2Fuc19hcm1lIiwic2NpZW50aWZpY0Rpc3BsYXkiOnRydWUsImNvbG9yIjoiI0VDNjQzQyJ9LHsidHlwZSI6ImNvbHVtbiIsImZ1bmMiOiJBVkciLCJ5QXhpcyI6InZvbHNfc2Fuc192aW9sZW5jZV9jb250cmVfZGVzX3BlcnNvbm5lcyIsInNjaWVudGlmaWNEaXNwbGF5Ijp0cnVlLCJjb2xvciI6IiNBQkNFRDkifSx7InR5cGUiOiJjb2x1bW4iLCJmdW5jIjoiQVZHIiwieUF4aXMiOiJjb3Vwc19ldF9ibGVzc3VyZXNfdm9sb250YWlyZXNfc3VyX3BlcnNvbm5lc19kZV8xNV9hbnNfb3VfcGx1cyIsInNjaWVudGlmaWNEaXNwbGF5Ijp0cnVlLCJjb2xvciI6IiNEMDUzNTYifSx7InR5cGUiOiJjb2x1bW4iLCJmdW5jIjoiQVZHIiwieUF4aXMiOiJjYW1icmlvbGFnZXNfZGVfbG9nZW1lbnQiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiIjNEY4RjU1In0seyJ0eXBlIjoiY29sdW1uIiwiZnVuYyI6IkFWRyIsInlBeGlzIjoidm9sc19kZV92ZWhpY3VsZXNfYXV0b21vYmlsZXNfb3VfZGV1eF9yb3Vlc19tb3RvcmlzZXMiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiIjMUI2Njk4In0seyJ0eXBlIjoiY29sdW1uIiwiZnVuYyI6IkFWRyIsInlBeGlzIjoidm9sc19kYW5zX2xlc192ZWhpY3VsZXMiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiIjQUEzQzQ0In0seyJ0eXBlIjoiY29sdW1uIiwiZnVuYyI6IkFWRyIsInlBeGlzIjoidm9sc19kX2FjY2Vzc29pcmVzX3N1cl92ZWhpY3VsZXMiLCJzY2llbnRpZmljRGlzcGxheSI6dHJ1ZSwiY29sb3IiOiIjRThBRjU1In1dLCJ4QXhpcyI6ImRlcGFydGVtZW50IiwibWF4cG9pbnRzIjo1LCJzb3J0Ijoic2VyaWUxLTIiLCJjb25maWciOnsiZGF0YXNldCI6ImNyaW1lcy1ldC1kZWxpdHMtZW5yZWdpc3RyZXMtcGFyLWxlcy1mb3JjZXMtZGUtc2VjdXJpdGUtZW4tMjAxNi1wYXItZGVwYXJ0ZW1lbnQiLCJvcHRpb25zIjp7fX19XSwidGltZXNjYWxlIjoiIiwiZGlzcGxheUxlZ2VuZCI6dHJ1ZSwiYWxpZ25Nb250aCI6dHJ1ZX0%3D"></iframe>

Source Opendatasoft: Nombre des crimes par département en france: https://www.interieur.gouv.fr/Interstats/Actualites/Insecurite-et-delinquance-en-2016-premier-bilan-statistique.  


## Tableau des Régions de France au taux de criminalité le plus élévé avec leur superfécie et la population. 
Nous avons Récupéré ces 5 régions de France au taux de criminalité le plus élevé ainsi que leur nombre de population et la superficie sur un fichier Excel . 

| Régions                                | Superficie | Taux de criminalité | Population        |
|----------------------------------------|------------|---------------------|-------------------|
| Nord-Pas-de-Calais-Picardie            | 31 813 km² | 10,64%              | 6 009 976         |
| Provence-Alpes-Côte d’Azur              | 31 400 km² | 9,71%               | 5 160 335         |
| Languedoc-Roussillon-Midi-Pyrénées     | 72 724 km² | 9,27%               | 6 004 624         |
| Aquitaine-Limousin-Poitou-Charentes    | 84 062 km² | 8,99%               | 6 003 982         |
| Bourgogne-Franche-Comté                | 47 784 km² | 8,79%               | 3 577 776         |


>>Tableau généré avec [Tables Generator](https://www.tablesgenerator.com)
Sources des informations : https://actu.fr/societe/carte-delinquance-et-criminalite-en-hausse-voici-les-departements-les-plus-touches_56998666.html / https://fr.statista.com/statistiques/499848/nombre-habitants-par-region-france/

## Visualisation :
Nous avons cette visualisation qui mets en avant le taux de polupation ainsi que le taux de ciminalité. Ce qui nous permet d'étudier le lien étroit qu'entretiennent ces deux variables. En conclusion, il semble que le nombre de population n'influe pas réellement le taux de criminalité .

<iframe title="[ Régions de France taux de criminalité / Population ]" aria-label="Multiple Pies" id="datawrapper-chart-wBG2J" src="https://datawrapper.dwcdn.net/wBG2J/2/" scrolling="no" frameborder="0" style="border: none;" width="600" height="388" data-external="1"></iframe>
 
>>> Généré par Datawapper

 # Crimes Raciaux  à New York <a name="NewYork"></a>  
 Nous sommes allés récupérer les jeux de données de l'open Data de New York .
 
 Dans ce graph, nous avonc filtré nos données selon le genre du criminel ( femme/homme) et les crimes raciaux. 
![Rawgraph Visualisation](https://raw.githubusercontent.com/thizirisaighi/M2_DEFI_SAIGHI_Thziri/main/viz(1).svg)
>>> Source: https://data.cityofnewyork.us/Public-Safety/NYPD-Hate-Crimes/bqiq-cu78



# Crimes dans le monde<a name="Monde"></a> 
Nous avosn récupéré les données dans deux fichiers excel  avec le taux de criminalité le plus élevé et le plus bas et nous avons combiné les deux pour en faire qu'un seul tableau . Nous avons ajouté les deux colonnes "Lat"et "Long".
Nous avons plusieurs sources pour récupérer l'ensemble de ces informations: Lat,Long, Population, taux de criminalité. 

| Pays                   | Taux de criminalité | LAT       | LONG      |
|------------------------|---------------------|-----------|-----------|
| Venezuela              | 82,08               | 6.4238    | -66.5897  |
| Papouasie-Nouvelle-Guinée | 80,38            | -6.315    | 143.9555  |
| Afghanistan            | 78,44               | 33.9391   | 67.71     |
| Haïti                  | 78,30               | 18.9712   | -72.2852  |
| Afrique du Sud         | 75,55               | -30.5595  | 22.9375   |
| Honduras               | 74,31               | 15.199999 | -86.241905|
| Trinité-et-Tobago      | 70,76               | 10.6918   | -61.2225  |
| Syrie                  | 69,08               | 34.8021   | 38.9968   |
| Guyane                 | 68,80               | 3.9339    | -53.1258  |
| Jamaïque               | 67,54               | 18.1096   | -77.2975  |
| Pérou                  | 67,53               | -9.19     | -75.0152  |
| Somalie                | 66,70               | 5.1521    | 46.1996   |
| Brésil                 | 66,13               | -14.235   | -51.9253  |
| Nigeria                | 65,84               | 9.082     | 8.6753    |
| Angola                 | 65,82               | -11.2027  | 17.8739   |
| Islande                | 1,80                | 64.9631   | -19.0208  |
| Japon                  | 0,20                | 36.2048   | 138.2529  |
| Singapour              | 0,30                | 1.3521    | 103.8198  |
| Danemark               | 1,00                | 56.2639   | 9.5018    |
| Norvège                | 1,10                | 60.472    | 8.4689    |
| Suisse                 | 1,50                | 46.8182   | 8.2275    |
| Finlande               | 1,70                | 61.9241   | 25.7482   |
| Canada                 | 1,80                | 56.1304   | -106.3468 |
| Suède                  | 1,90                | 60.1282   | 18.6435   |
| Nouvelle-Zélande       | 2,10                | -40.9006  | 174.886   |

>>Tableau généré avec [Tables Generator](https://www.tablesgenerator.com) Source1: https://fr.mapsofworld.com/world-top-ten/countries-with-highest-reported-crime-rates.html/Source2: https://www.geo.fr/voyage/un-classement-fait-letat-des-pays-les-plus-dangereux-du-monde-214513/Source3: https://fr.wikipedia.org/wiki/Liste_des_pays_par_population/Source4: https://www.presentation-cv-simple.com/quel-est-le-pays-avec-le-plus-bas-taux-de-criminalite/

## Les pays du monde au taux de criminalité le plus élevé  
<iframe title="[ Les pays du monde au taux de criminalité le plus élevé  ]" aria-label="Interactive line chart" id="datawrapper-chart-ZMMhE" src="https://datawrapper.dwcdn.net/ZMMhE/1/" scrolling="no" frameborder="0" style="border: none;" width="600" height="400" data-external="1"></iframe>
>> Généré par Datawapper

## Cartes des régions du monde au taux de criminalité du plus élevé au plus bas  : 
<iframe title="[ Cartes Taux de criminalité dans le monde   ]" aria-label="Map" id="datawrapper-chart-wXqzv" src="https://datawrapper.dwcdn.net/wXqzv/1/" scrolling="no" frameborder="0" style="border: none;" width="600" height="381" data-external="1"></iframe>
>> Généré par Datawapper

## Les 7 continents 

<iframe title="Les 7 continents " aria-label="Multiple Donuts" id="datawrapper-chart-gkvjn" src="https://datawrapper.dwcdn.net/gkvjn/1/" scrolling="no" frameborder="0" style="border: none;" width="600" height="418" data-external="1"></iframe>

### Pourquoi avons nous voulu faire cette représentation des continents ? 

 ces indicateurs peuvent  être affectés par des facteurs sociaux communs tels que le niveau de développement, la qualité des services publics, ou la stabilité sociale, il est important de noter qu'ils ne sont pas intrinsèquement liés de manière causale. Une société peut avoir un taux de mortalité élevé sans nécessairement avoir un taux de criminalité élevé, et vice versa. Les indicateurs doivent être compris dans leur contexte spécifique pour tirer des conclusions significatives sur le niveau de sécurité et de bien-être dans une société donnée.



# Tableau des tueurs en série qui ont marqué l'histoire <a name="Histoire"></a> 

| Nom            | Âge | Nationalité | Genre  |
|----------------|-----|-------------|--------|
| Josef Mengele  | 67  | Allemand    | Homme  |
| Gilles Bertin   | 58  | Français    | Homme  |
| Charles Manson  | 83  | Américain   | Homme  |
| Al Capone       | 48  | Américain   | Homme  |
| Ted Bandy       | 42  | Américain   | Homme  |
| Jeffrey Dahmer  | 34  | Américain   | Homme  |
| Lucky Luciano   | 66  | Italien     | Homme  |
| Albert Fish     | 65  | Américain   | Homme  |
| Emile Louis      | 79  | Français    | Homme  |
| Bonnie Parker    | 23  | Américaine  | Femme |
| Anne Perry       | 84  | Anglaise    | Femme |
| Lisa M.Montgo    | 52  | Américain   | Femme |
| Phil Spector     | 81  | Américaine  | Homme  |
| Kang Kek Ieu     | 77  | Cambodge    | Homme  |
| Richard Blass    | 29  | Canada      | Homme  |
| Peter Sutcliffe  | 74  | Londres     | Homme  |
| Thierry Paulin   | 22  | Français    | Homme  |
| Andrex Cunanan   | 27  | Américain   | Homme  |
| Griselda Blanco  | 69  | Colombie    | Femme |


>>Tableau généré avec [Tables Generator](https://www.tablesgenerator.com)
Source : https://www.jesuismort.com/cimetiere/criminel-et-criminelle

## La visulaisation du tableau avec un filtre sur les hommes et les femmes .

<iframe src='https://flo.uri.sh/visualisation/16607087/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/visualisation/16607087/?utm_source=embed&utm_campaign=visualisation/16607087' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>

### Jeffrey Dhamer
![Jeffrey Dahmer](https://github.com/thizirisaighi/M2_DEFI_SAIGHI_Thziri/blob/main/Jeffrey_Dahmer.jpg?raw=true)
>>> Source : https://encrypted-tbn3.gstatic.com/images?q=tbn:ANd9GcSYceJVurGKK4AP8QNn5BI4U-8RvAbLk28ji5iwdjklEjPeYrAf


Jeffrey Dahmer, également connu sous le nom de "The Milwaukee Cannibal" ou "The Milwaukee Monster", était un criminel américain notoire et un tueur en série. Né le 21 mai 1960 à Milwaukee, Wisconsin, Dahmer a été reconnu coupable d'avoir commis le meurtre de 17 jeunes hommes entre 1978 et 1991. Ses crimes incluaient le meurtre, le démembrement et la mutilation de ses victimes.

Dahmer a été arrêté en 1991 et condamné à 16 peines de réclusion à perpétuité. En prison, il a été battu à mort par un autre détenu en 1994.

Les crimes de Jeffrey Dahmer ont choqué le public en raison de leur brutalité et de la nature choquante des actes qu'il a commis. Dahmer a été décrit comme l'un des tueurs en série les plus notoires de l'histoire criminelle américaine.
 
## Voici les 15 premières victimes de Jeffrey Dahmer:

<iframe src='https://flo.uri.sh/visualisation/16630213/embed' title='Interactive or visual content' class='flourish-embed-iframe' frameborder='0' scrolling='no' style='width:100%;height:600px;' sandbox='allow-same-origin allow-forms allow-scripts allow-downloads allow-popups allow-popups-to-escape-sandbox allow-top-navigation-by-user-activation'></iframe><div style='width:100%!;margin-top:4px!important;text-align:right!important;'><a class='flourish-credit' href='https://public.flourish.studio/visualisation/16630213/?utm_source=embed&utm_campaign=visualisation/16630213' target='_top' style='text-decoration:none!important'><img alt='Made with Flourish' src='https://public.flourish.studio/resources/made_with_flourish.svg' style='width:105px!important;height:16px!important;border:none!important;margin:0!important;'> </a></div>
>>> Généré par Flourish Source : https://www.urban-fusions.fr/qui-etait-les-victimes-de-jeffrey-dahmer-et-pourquoi-prenait-il-des-photos/

# Conclusion <a name="Conclusion"></a> 
Il est important de noter que l'idée que les criminels, en particulier ceux qui ont commis des actes graves, peuvent vivre de manière normale et souriante parmi nous est complexe. Certains individus peuvent masquer habilement leurs activités criminelles derrière une apparence de normalité comme le cas deJffrey Dahmer entre autres, , utilisant souvent des mécanismes d'adaptation sociaux pour se fondre dans la société. Cela peut rendre difficile la détection de comportements criminels.

Il est également crucial de se rappeler que l'apparence extérieure ne reflète pas toujours la réalité profonde d'une personne. Les criminels, même ceux qui semblent vivre normalement, peuvent être en proie à des problèmes psychologiques, des troubles mentaux ou des motivations complexes qui ne sont pas immédiatement apparents.

La société doit donc rester vigilante et consciente de la diversité des comportements humains. Les autorités chargées de l'application de la loi, les professionnels de la santé mentale et la communauté dans son ensemble jouent un rôle essentiel dans la détection précoce, la prévention et le traitement des comportements criminels. Une compréhension approfondie de ces questions est nécessaire pour maintenir la sécurité publique et aider ceux qui peuvent être enclins à des comportements déviants à trouver un soutien approprié.
  
 
