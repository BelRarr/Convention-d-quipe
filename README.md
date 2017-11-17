# Conventions d'équipe

## Pourquoi du code de qualité ?
-	Au fur et à mesure que le désordre augmente, la productivité tend vers 0 
-	Un développeur passe 10 fois plus de temps à lire du code qu’à en écrire 
-	Les conséquences du code sale se manifestent progressivement 
-	Notre ennemi numéro 1 en informatique : la complexité inutilement accumulée
![productivity](./img/productivity.jpg)


## Meilleure métrique pour mesurer de la qualité du code : WTFs/Minute
![WTF](./img/WTF.jpg)
* WTF : Acronyme anglais pour « C’est quoi ce bazard !!? »

## Qu’est-ce que du code sale ?
-	Un marécage où on se perd
-	Aussi loin qu’on avance à la recherche d’un indice, 
tout ce que l’on voit c’est du code sans signification
-	Du code sans structure
-	Du code dupliqué
-	Un patchwork 1000 fois reprisé
-	Complexité inutile
-	Structures de données mal adaptées au besoin
-	Commentaires inappropriés

## Qu’est-ce que du code propre ?
-	Ce qui se conçoit bien s’énonce clairement et les mots pour le dire viennent aisément. Nicolas Boileau 
-	Si vous n'êtes pas capable d'expliquer quelque chose à un enfant de 6 ans, c'est que vous ne le comprenez pas vous-même. Einstein
-	Il semble que la perfection soit atteinte non quand il n'y a plus rien à ajouter, mais quand il n'y a plus rien à retirer. St Exupéry
### Lisible
- Se lit comme une phrase. Les abstractions sont nettes, les chemins d’exécution évidents.
- Qu’est ce qui est le plus facile à lire ?
```c#
public List<int[]> getThem(List<int[]> theList){
  List<int[]> list1 = new ArrayList<int[]>();
  foreach (int[] x in theList)
     if (x[0] == 4)
       list1.Add(x);
  return list1;
}
```
```c#
public List<Cell> getFlaggedCells(List<Cell> gameBoard){
  List<Cell> flaggedCells = new ArrayList<Cell>();
  foreach (Cell cell in gameBoard)
    if (cell.isFlagged())
      flaggedCells.Add(cell);
  return flaggedCells;
}
```
```c#
public List<Cell> getFlaggedCells(List<Cell> gameBoard){
  return gameBoard.Where(cell => cell.isFlagged());
}
```
### Élégant
- Assez simple et direct pour ne pas laisser de place aux bugs.
### Facile à modifier
- Peut être modifié par un autre que son auteur, utilise un nommage explicite et expressif.
### Écrit avec soin
- Aucun problème évident ne saute aux yeux.
### Sans surprise
- Le corps des méthodes est ce que l’on avait deviné

# Lean Canvas

The Lean Canvas is a version of the Business Model Canvas adapted by Ash Maurya specifically for startups. You can read more about it [here](http://leanstack.com/why-lean-canvas/).

<table>
  <tr>
    <td rowspan="2">
      <b>Problem</b>
      <p>Top 3 Problems</p>
    </td>
    <td>
      <b>Solution</b>
      <p>Top 3 features</p>
    </td>
    <td rowspan="2" colspan="2">
      <b>Unique Value Proposition</b>
      <p>Single, clear, <br>
      compelling message <br>
      that states why you <br>
      are different and <br>
      worth paying <br>
      attention</p>
      <br><br><br><br><br>
    </td>
    <td>
      <b>Unfair Advantage</b>
      <p>Can't be easily <br>
      copied or bought</p>
    </td>
    <td rowspan="2">
      <b>Customer Segments</b>
      <p>Target customers</p>
    </td>
  </tr>
  <tr>
    <td>
      <b>Key Metrics</b>
      <p>Key activities you measure</p>
    </td>
    <td>
      <b>Channels</b>
      <p>Path to customers</p>
    </td>
  </tr>
  <tr>
    <td colspan="3">
      <b>Cost Structure</b>
      <p>Customer Acquisition Costs <br>
      Distribution Costs <br>
      Hosting <br>
      People, etc.</p>
    </td>
    <td colspan="3">
      <b>Revenue Streams</b>
      <p>Revenue Model <br>
      Life Time Value <br>
      Revenue <br>
      Gross Margin</p>
    </td>
  </tr>
</table>
