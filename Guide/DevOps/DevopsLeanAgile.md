# DevOps ? Lean ? Agile ?

DevOps suscite de l’intérêt, des craintes, et de la confusion.
- De l’intérêt : c'est un mot 'à la mode', on en ressent le potentiel sans vraiment pouvoir l’expliquer
- Des craintes :
    - La « boîte à outils » DevOps est technique, n’est-ce pas un nouveau trip techno ?
    - Les clients des services TI rêvent de simplicité, regrettent le temps où ils ne dépendaient pas des services TI, où ils embauchaient un stagiaire qui implémentait les logiques métiers dans un fichier Excel ! DevOps semble ajouter de la lourdeur.
- De la confusion :
    - Nous avons les méthodes traditionnelles, Macroscope, l’agilité, le Lean, ITIL, c’est déjà compliqué. Où se situe DevOps dans tout cela ? Pourquoi ajouter de nouveaux termes ?
    - Qu’est-ce réellement DevOps ? Chacun semble avoir ses définitions, généralement selon ce qu’il a à vendre.
    - Beaucoup d’outils, difficile de savoir comment le mettre en place et quels en étaient les gains concrets

Bref, difficile de s’y retrouver !

# Qu’est-ce que DevOps ? 

## Du Lean appliqué aux TI
- L’agilité répondrait très bien au « quoi ? », « Qu’est-ce qu’on fait ? »
- Le Lean répondrait très bien au « Pourquoi ? », permettrait d’identifier les relations de causes à effets décisions – conséquences, permettrait par exemple d’expliquer les gains recherchés de chacune des routines scrum (c’est motivant de comprendre pourquoi)
- DevOps répondrait très bien au « Comment ? », beaucoup de pratiques d’ingénierie sont dans le catalogue DevOps pour répondre aux défis que posent l’agilité et le Lean
- l’agilité, le lean et DevOps sont interliés (Safe 4.5 donne une belle vue d’ensemble de mon point de vue)
- Les pratiques d’ingénierie DevOps pourrait avoir des effets bénéfiques sur des projets Waterfall même si cela en limiterait les bénéfices.
## Une approche visant à créer des cercles vertueux coût-qualité-délais-motivation
- En mode projet, on choisit généralement d’en sacrifier 1, généralement le moins quantifiable : la qualité
- En effet, les métriques de qualités pour les projets à une seule livraison finale arrivent après les projets : succès des déploiements, nombre d’incidents lié au changement, utilisation réelle des fonctionnalités par les utilisateurs, gains de productivité réels pour les utilisateurs.
- Ainsi les projets optimisent les couts-délais et les équipes de support tentent de faire barrage pour préserver la stabilité
- L’approche DevOps a pour but de casser ce schéma

## L’union des personnes, processus et outils vers un but commun : livrer de la valeur en continue au client 

### Alignement,
-  Les problèmes de qualité deviennent la responsabilité de tous
-  Le rôle du département qualité ne se limite plus à bloquer en bout de chaîne mais devient proactif, un « coach de la qualité en continu »
-  La qualité dans le sens « pas de problème caché, pas d’escroquerie » agit sur la confiance des intervenants, des partenaires

### Transparence, les problèmes de qualité
-  ont un cout 
-  sont considérés comme un délai supplémentaire pour les utilisateurs (pour eux, le chrono s’arrête quand ils commencent à l’utiliser !)
-  deviennent rapidement visibles, notamment avec de tests en continu
-  sont adressés jusqu’à la cause racine

### Consistance
-  Pour diagnostiquer efficacement des problèmes, il est nécessaire de connaître les écarts entre
    - Avant / après un changement
    - Les différents environnements pour une même livraison
-  Cela implique que les procédures d’installation d’un environnement et de déploiements d’une livraison doivent
    - Être comprises et challengées par le plus d’intervenant possibles
    - Être rigoureusement suivies
-  On parle de procédures d’installation « Exécutables », comprise par les humains, exécutées par les machines, le meilleur des 2 mondes.
-  Ces procédures doivent être exécutées fréquemment pour en garantir leur fiabilité

### Réduction des risques 
-  Les premiers points permettent déjà de réduire les risques
-  D’autres techniques existent :
    - Possibilité d’activer / désactiver des fonctionnalités par paramétrage jusqu’à l’adoption complète de la fonctionnalité. Par extension les fonctionnalités peuvent être actives pour un certains groupe d’utilisateur, puis par groupe d’utilisateur de plus en plus large
    - Monitoring pour être proactif sur les erreurs, par exemple détection d’incohérences des données en base de données

### Limitation du gaspillage
- Monitoring possible sur la réelle utilisation des fonctionnalités suivi par une enquête si une fonctionnalité n’est pas utilisée pour comprendre. Si la fonctionnalité n'est pas utilisé pour de bonnes raisons, inutile de développer des fonctionnalités équivalentes !

# Pour aller plus loin
- Les principaux acteurs du mouvement DevOps ont écrit un livre de référence : « The DevOps Handbook », je vous le recommande !
- Pour connaître les gains économiques concrets de DevOps, je vous recommande le livre de Donald Reinertsen « The Principles of Product Development Flow: Second Generation Lean Product Development ». 
