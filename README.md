# Conventions d'équipe

## La règle du Boy Scout
- Laisser le code source plus propre que ce que vous l’avez trouvé.

| Pourquoi du code de qualité ?   | Le WTFs/Minute pour mesurer de la qualité du code |
|:----------|:----------|
| ![productivity](./img/productivity.jpg) | ![WTF](./img/WTF.jpg) |
|	Au fur et à mesure que le désordre augmente, la productivité tend vers 0 | * WTF : Acronyme anglais pour « C’est quoi ce bazard !!? |
|	Les conséquences du code sale se manifestent progressivement |	Un développeur passe 10 fois plus de temps à lire du code qu’à en écrire |
|	Notre ennemi numéro 1 en informatique : la complexité inutilement accumulée |

## Qu’est-ce que du code propre ?
| Qu’est-ce que du code sale ?   | Qu’est-ce que du code propre ? |
|:----------|:----------|
|	Un marécage où on se perd | Ce qui se conçoit bien s’énonce clairement et les mots pour le dire viennent aisément. Nicolas Boileau !
|	Aussi loin qu’on avance à la recherche d’un indice, tout ce que l’on voit c’est du code sans signification| 
|	Du code sans structure | Si vous n'êtes pas capable d'expliquer quelque chose à un enfant de 6 ans, c'est que vous ne le comprenez pas vous-même. Einstein |
|	Du code dupliqué | Il semble que la perfection soit atteinte non quand il n'y a plus rien à ajouter, mais quand il n'y a plus rien à retirer. St Exupéry |
|	Un patchwork 1000 fois reprisé
|	Complexité inutile | |
|	Structures de données mal adaptées au besoin
|	Commentaires inappropriés

-	Ce qui se conçoit bien s’énonce clairement et les mots pour le dire viennent aisément. Nicolas Boileau 
-	Si vous n'êtes pas capable d'expliquer quelque chose à un enfant de 6 ans, c'est que vous ne le comprenez pas vous-même. Einstein
-	Il semble que la perfection soit atteinte non quand il n'y a plus rien à ajouter, mais quand il n'y a plus rien à retirer. St Exupéry

| Principe   | Description |
|:----------|:----------|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Lisible | Se lit comme une phrase. Les abstractions sont nettes, les chemins d’exécution évidents. |
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Élégant | Assez simple et direct pour ne pas laisser de place aux bugs.|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Facile à modifier | Peut être modifié par un autre que son auteur, utilise un nommage explicite et expressif.|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Écrit avec soin | Aucun problème évident ne saute aux yeux.|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Sans surprise | Le corps des méthodes est ce que l’on avait deviné.|

- Qu’est ce qui est le plus facile à lire ?
<table>
<tr>
<td>
   <pre lang="csharp">
public List<int[]> getThem(List<int[]> theList){
  List<int[]> list1 = new ArrayList<int[]>();
  foreach (int[] x in theList)
     if (x[0] == 4)
       list1.Add(x);
  return list1;
}

   </pre>
</td>
<td>
  <pre lang="csharp">
public List<Cell> getFlaggedCells(List<Cell> gameBoard){
  List<Cell> flaggedCells = new ArrayList<Cell>();
  foreach (Cell cell in gameBoard)
    if (cell.isFlagged())
      flaggedCells.Add(cell);
  return flaggedCells;
}
  </pre>
</td>
<td>
  <pre lang="csharp">
public List<Cell> getFlaggedCells(List<Cell> gameBoard){
  return gameBoard.Where(cell => cell.isFlagged());
}
  </pre>
</td>
</tr>
</table>
  
## Qu’est-ce que du design sale ?
| Principe   | Description |
|:----------|:----------|
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Rigide | Les changements simples doivent être propagés dans beaucoup de modules dépendants ; ce qui rend les changements simples fastidieux.|
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Fragile | Un petit changement cause beaucoup d’effets de bords. Par peur de modifier et casser, on patche ce qui entraîne de nouveaux effets de bords.|
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Immobile | Réutiliser du code nécessite trop d’effort et de risque à cause des dépendances,  alors on copie-colle… |
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Visceux | Lors d’un changement à effectuer, nous sommes face au dilemme suivant : devons-nous préserver l’architecture en place et perdre du temps ou prendre des raccourcis et gagner du temps ? |
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Inutilement Complexe | La conception contient des éléments non utiles, souvent dans le but d’éviter les autres problèmes de design (abstractions non utiles par anticipation). |
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Contient de la duplication inutile | Ici, on est dans la POCC (Programmation Orienté Copier-Coller). De l’abstraction ou de la composition aurait dû être faite.| 
| ![#f03c15](https://placehold.it/15/f03c15/000000?text=+) Opaque | Le code est difficile à comprendre. Beaucoup de temps est investi en « reverse engineering » pour le comprendre et/ou les modifications de code introduisent des bugs dues à la non-compréhension.|
## Principes élémentaires pour du design propre 

| Principe   | Description |
|:----------|:----------|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Garde ça stupidement simple! (KISS) | <ul><li>Toute complexité non indispensable devrait être évitée.</li><li>Ne pas optimiser quoi que ce soit avant de maîtriser totalement une version simple de ce que l'on crée.</li><li>Notre ennemi numéro 1 en informatique : la complexité !</li></ul>|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Vous n’en aurez pas besoin! (YAGNI) | Mettez toujours en œuvre les choses quand vous en avez effectivement besoin, pas lorsque vous prévoyez simplement que vous en aurez besoin.|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Ne vous répétez pas (DRY) | Toute connaissance doit avoir une représentation unique, non-ambiguë, faisant autorité.|


## Principes plus avancés de design propre (Jedi)
| Principe   | Description |
|:----------|:----------|
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Programmation Orienté Objet (POO) | 2 outils fournis par la POO pour attaquer la complexité : la composition et l’abstraction. L’abstraction est souvent surutilisée au détriment de la composition. <ul><li>Abstraction : « Des objets se comportent presque pareil »</li><li>Composition : Des tâches similaires sont déléguées à un objet fils (ex : logger, publisher).</li></ul> |
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Principes SOLID | Les principes SOLID nous aident à exploiter la POO et nous guide vers une architecture modulaire : Le code s’assemble comme des blocs LEGO. |
| ![#c5f015](https://placehold.it/15/c5f015/000000?text=+) Principes GRASP | Les principes GRASP mettent un focus sur les responsabilités d’un composant, qu’est-ce qui doit être mis où. Le résumé serait « Chaque chose a sa place et chaque place a sa chose ». |

