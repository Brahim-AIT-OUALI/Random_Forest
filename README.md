# Random Forests
#### Théorie et intuition : motivation et histoire.
#### Les Random Forests s'inscrivent dans l'amélioration d'un seule arbre de décision unique. 
- Imaginez un dataset avec des features et un label:
  
![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/691c1d31-34d2-449a-afc2-f029fd801efc)

- Arbre de décision limité par le critère d'information ( l'impureté de Gini = critère de division le plus courant, un autre = gain d'information)
- limité par l'impureté de Gini ce qui signifie non utilisation de toutes les features. 

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/734609f6-f376-4c29-bf75-c73ffe2fe28b)

- Le noeud racine sera toujours le même! Pour les mêmes règles c'est à dire le même critère d'information, la même profondeur maximale, le même nombre de division autorisées etc, l'arbdre de division unique sera le même donc le noeud racine sera le même
- La feature de la racine a une grande influence sur l'arbre.
  
![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/623163d8-b670-4d82-a7c0-556463f4fb8d)

#### Nous pourrions essayer d'adapter les règles, par exemple :
 - Critère de division (gain d'information au lieu de l'impureté de Gini)
 - Diminution de l'impureté minimale de Gini.
 - Définition des limites de profondeur
 - Limitation du nombre de feuilles terminaux
#### Mais pour chaque ensemble de règles, il n'y a qu'un seul arbre de décision possible.
- Cependant, avec tous ces ajustements d'hyperparamètres, l'arbre de décision unique reste limité:
   - Feature unique pour le noeud racine
   - Le critère de division peut conduire à la non-utilisation de certaines features.
   - Risque d'overfitting aux données.
### Principe des Randoms Forets: 
Arbre de décision unique = certaines features ne sont pas utilisées. il serait inétressant d'avoir une sorte de signal ou d'information dans ces données afin de pouvoir les utiliser.

#### idée = étendre un arbre de décision unique à un ensemble d'estimateurs, c'est-à-dire  plusieurs arbres de décision constituant justement Random Forest ou forêt aléatoire.


![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/542f9f8e-d48e-4723-be04-694c0c30da79)
![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/9b45da29-34b2-4fe3-b384-ccb070e496c2)

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/322523ac-2cc8-4560-bf4f-0bbb7322578f)

- ### Idée principale des Randoms Forests:
  - Créer des sous-ensembles de features sélectionnées de manière aléatoire pour chaque division poteltielle
#### Choisir un nombre N de features à sélectionner aléatoirement pour un sous-ensemble. 
#### Dans notre exemple N  = 3, à partir de ces 3 features, je commence par construire un arbre de décision sur ma première division (=noeud racine)
#### On voit ainsi comment on évite d'avoir la même feature au noeud racine en fonction des critères d'information.
#### Sur la base de mes critères d'information tels que le gain d'information ou l'impureté de Gini, la meilleure feature sur laquelle on divise dans un premier temps est la feature jaune.
![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/dd7c7ec3-fb14-4114-8f5b-ac313353426e)

#### On se trouve maintenant sur un autre **noeud**:

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/a954d899-9b03-4c8a-8610-8f7359245728)

je dois décider ou non de diviser à nouveau. Si je décide sur la base des critères de mon arbre de décision tels que le gain d'information ou l'impureté de Gini que j'ai besoin d'effectuer une division, je choisis un autre sous-ensemble de features pour la division. 
#### Puis j'utilise mes critères d'information pour décider lesquelles de ces caractéristiques de ce sous-ensemble aléatoire je dois choisir pour poursuivre la division
#### Dans ce cas, je peux choisir la feature orange et obtenir une diminution de l'impureté de Gini suffisante pour continuer et diviser cela en noeuds feuilles et en noeuds terminaux.

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/0c056817-9ebf-49b9-9d57-9da0119f8c8c)

#### Même chose pour l'autre **noeud** :

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/3b1594fb-29a2-4d34-b918-09d1a566fa27)


- Choix d'autre sous-ensemble aléatoire de features et je choisis la meilleure feature de ce sous-ensemble pour continuer les tâches de division jusqu'à ce que je construit mon arbre.

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/cf98e75b-1b4e-4984-9aa5-b56f02beb1a5)

#### Grâce à cette idée très puissante de choisir des sous ensembles de features sélectionnés de manière aléatoire, je vais m'assurer de ne pas surentraîner ces arbres. En fait, la possibilité de choisir ces sous ensembles aléatoires de features me permet d'explorer de nombreux aspects différents de l'ensemble de mon espace de features. Il est fort probable que je pourrais utiliser toutes les features qui contiennent un signal utile, car si elles ont un signal utile , même si elles ne sont pas toujours utilisées pour le nœud racine, je sais qu'à terme, en fonction du nombre d'arbres que je construirais, j'examinerai cette feature , et si elle est importante, je choisirai de m'en servir. Ce qui me permet de créer cette forêt ou cet ensemble de plusieurs types d'arbres de décision qui se développent de différentes manières, car je sais qu'ils examinent différents sous-ensembles de données chaque fois qu'ils doivent décider d'une division. 
#### Et j atténue également le problème de la non-utilisation des features utiles. 
#### Je sais que si je construis suffisamment d'arbres, toute feature utile finira par être utilisée parce qu'elle aura été sélectionnée dans un sous ensemble aléatoire pour une certaine division. 

<img width="527" alt="image" src="https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/ffd80da8-fdb5-4837-b9ad-c9cbc9a68bcf">


### - Question : comment obtenir une réponse ou une prédiction à partir de nombreux modèles ?
 - Si classification : vote
![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/52d485f7-269f-44ad-8185-03ef3851b98c)

 - Si régression : moyenne

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/e5ea8708-7855-42b3-9cfe-d1c3248df3ae)

### L'ajout d'une contraine de sous-espace de features aléatoires pouvait permettre aux arbres de croître beaucoup plus profondément sans provoquer d'overfitting.
























