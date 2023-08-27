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
