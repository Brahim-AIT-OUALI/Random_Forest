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

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/542f9f8e-d48e-4723-be04-694c0c30da79)
![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/9b45da29-34b2-4fe3-b384-ccb070e496c2)

![image](https://github.com/Brahim-AIT-OUALI/Random_Forest/assets/115220907/322523ac-2cc8-4560-bf4f-0bbb7322578f)




