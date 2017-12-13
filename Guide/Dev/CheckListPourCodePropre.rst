.. |RED| image:: /img/red.png
   :height: 11
   :width: 11
.. |GREEN| image:: /img/green.png
   :height: 11
   :width: 11
   
===== 
CheckList pour du code propre 
===== 
L'essentiel 
-------- 

+--------------------------+----------------------------------------+---------------------------------------------------------------+
|  Principe                |  |RED| Pas bien                        | |GREEN| Bien                                                  |
+--------------------------+----------------------------------------+---------------------------------------------------------------+
|                          | .. code-block:: csharp                 | .. code-block:: csharp                                        |
|                          |                                        |                                                               |
|  - Des noms prononçables |   class DtaRcrd102{                    |  class Customer{                                              |
|                          |     private DateTime genymdhms;        |    private DateTime generationTimestamp;                      |
|                          |     private DateTime modymdhms;        |    private DateTime modificationTimestamp;                    |
|                          |     private String pszqint = "102";    |    private String recordId = "102";                           |
|                          |     /* ... */                          |     /* ... */                                                 |
|                          |   };                                   |  };                                                           |
|                          |                                        |                                                               |
+--------------------------+----------------------------------------+---------------------------------------------------------------+
|                          | .. code-block:: csharp                 | .. code-block:: csharp                                        |
|                          |                                        |                                                               |
| - Utiliser des constantes|   int s = 0;                           |  int realDaysPerIdealDay = 4;                                 |
|                          |   for (int j = 0; j < 34; j++){        |  const int WORK_DAYS_PER_WEEK = 5;                            | 
|                          |     s += (t[j] * 4) / 5;               |  int sum = 0;                                                 |
|                          |   }                                    |  for (int j = 0; j < NUMBER_OF_TASKS; j++){                   |
|                          |                                        |    int realTaskDays = taskEstimate[j] *                       |
|                          |                                        |                       realDaysPerIdealDay;                    |
|                          |                                        |    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);       |
|                          |                                        |    sum += realTaskWeeks;                                      |
|                          |                                        |  }                                                            |
+--------------------------+----------------------------------------+---------------------------------------------------------------+
|                          | .. code-block:: csharp                 | .. code-block:: csharp                                        |
|                          |                                        |                                                               |
| - Éviter les effets de   |   public Boolean checkPassword(        |    public Boolean checkPassword(                              |
|   bords. Pas bien à cause|     String userName, String password){ |      String userName, String password){                       |
|   de Session.initialize  |      User user =                       |       User user =                                             |
|                          |       UserGateway.findByName(userName);|        UserGateway.findByName(userName);                      |
|                          |      if (user != null) {               |       if (user != null) {                                     |
|                          |         /* ... */                      |          /* ... */                                            |
|                          |         Session.initialize();          |          return true;                                         |
|                          |         return true;                   |      };                                                       |
|                          |      };                                |      return false;                                            |
|                          |      return false;                     |    }                                                          |
|                          |   }                                    |                                                               |
+--------------------------+----------------------------------------+---------------------------------------------------------------+
|                          | .. code-block:: csharp                 | .. code-block:: csharp                                        |
|                          |                                        |                                                               |
| - Mettre du contexte     |  private void printGuessStatistics(    |  public class GuessStatisticsMessage {                        |
|   pertinent              |            char candidate, int count){ |    private String number;                                     |
|                          |    String number;                      |    private String verb;                                       |
|                          |    String verb;                        |    private String pluralModifier;                             |
|                          |    String pluralModifier;              |    public String make(char candidate, int count) {            |
|                          |    if (count == 0) {                   |       createPluralDependentMessageParts(count);               |
|                          |      number = "no";                    |       return String.Format(                                   |
|                          |      verb = "are";                     |         "There %s %s %s%s",                                   |
|                          |      pluralModifier = "s";             |         verb, number, candidate, pluralModifier);             |
|                          |    }                                   |    }                                                          |
|                          |    else if (count == 1) {              |    private void createPluralDependentMessageParts(int count) {|
|                          |      number = "1";                     |      if (count == 0)        { thereAreNoLetters(); }          |
|                          |      verb = "is";                      |      else if (count == 1)   { thereIsOneLetter();  }          |
|                          |      pluralModifier = "";              |      else                   { thereAreManyLetters(count); }   |
|                          |    }                                   |    }                                                          |
|                          |    else {                              |    private void thereAreManyLetters(int count) {              |
|                          |      number = count.ToString();        |      number = count.ToString();                               |
|                          |      verb = "are";                     |      verb = "are";                                            |
|                          |      pluralModifier = "s";             |      pluralModifier = "s";                                    |
|                          |    }                                   |    }                                                          |
|                          |    String guessMessage = String.Format(|    private void thereIsOneLetter() {                          |
|                          |      "There %s %s %s%s",               |      number = "1";                                            |
|                          |        verb,                           |      verb = "is";                                             |
|                          |        number,                         |      pluralModifier = "";                                     |
|                          |        candidate,                      |    }                                                          |
|                          |        pluralModifier);                |    private void thereAreNoLetters() {                         |
|                          |    Console.Write(guessMessage);        |      number = "no";                                           |
|                          |  }                                     |      verb = "are";                                            |
|                          |                                        |      pluralModifier = "s";                                    |
|                          |                                        |    }                                                          |
|                          |                                        |  }                                                            |
+--------------------------+----------------------------------------+---------------------------------------------------------------+
|                          | .. code-block:: javascript             | .. code-block:: javascript                                    |
|                          |                                        |                                                               |
| - Guard clause           |  response = server.Call(request)       |  response = server.Call(request)                              |
|                          |  if response.GetStatus() == RPC.OK:    |                                                               |
|                          |    if response.GetAuthorizedUser():    |  if response.GetStatus() != RPC.OK:                           |
|                          |      if response.GetEnc() == 'utf-8':  |    raise RpcError(response.GetStatus())                       |
|                          |        if response.GetRows():          |                                                               |
|                          |          vals = [ParseRow(r) for r in  |  if not response.GetAuthorizedUser():                         |
|                          |                  response.GetRows()]   |    raise ValueError('wrong encoding')                         |
|                          |          avg = sum(vals) / len(vals)   |                                                               |
|                          |          return avg, vals              |  if response.GetEnc() != 'utf-8':                             |
|                          |        else:                           |    raise AuthError('unauthorized')                            |
|                          |          raise EmptyError()            |                                                               |
|                          |      else:                             |  if not response.GetRows():                                   |
|                          |        raise AuthError('unauthorized') |    raise EmptyError()                                         |
|                          |    else:                               |                                                               |
|                          |      raise ValueError('wrong encoding')|  vals = [ParseRow(r) for r in                                 |
|                          |  else:                                 |          response.GetRows()]                                  |
|                          |    raise RpcError(response.GetStatus())|  avg = sum(vals) / len(vals)                                  |
|                          |                                        |  return avg, vals                                             |
+--------------------------+----------------------------------------+---------------------------------------------------------------+
|  Principe                | Description                                                                                            |
+--------------------------+--------------------------------------------------------------------------------------------------------+
| - Nommage                | * Classes :                                                                                            |
|                          |                                                                                                        |
|                          |   - Le nom des classes doivent être des noms ou des noms-phrases                                       |
|                          |                                                                                                        |
|                          |   - Éviter les verbes                                                                                  |
|                          |                                                                                                        |
|                          |   - Éviter Manager, Processor, Data, Info (Trop vague)                                                 |
|                          |                                                                                                        |
|                          | * Méthodes :                                                                                           |
|                          |                                                                                                        |
|                          |   - Le nom des méthodes doivent être des verbes ou des verbes phrases                                  |
|                          |                                                                                                        |
|                          |   - Éviter les verbes trop vagues                                                                      |
|                          |                                                                                                        |
+--------------------------+--------------------------------------------------------------------------------------------------------+
| - Découpage              |  * Pas de « grosse classe qui fait tout ». Une classe a un rôle clair et précis.                       |
|                          |                                                                                                        |
|                          |  * Les méthodes ne doivent faire qu’une chose et une seule (responsabilité unique)                     |
|                          |                                                                                                        |
|                          |  * Si plus de 2 paramètres par méthode :                                                               |
|                          |                                                                                                        |
|                          |    - serait-il pertinent de déléguer le travail à un objet fils ? (se poser la question)               |
|                          |                                                                                                        |
|                          |    - Minimiser les boucles imbriquées et préférer la création de nouvelles fonctions                   |
|                          |                                                                                                        |
|                          |  * Command and Query Separation (CQS)                                                                  |
|                          |                                                                                                        |
|                          |    - Une méthode doit soit                                                                             |
|                          |                                                                                                        |
|                          |    - retourner un résultat sans modifier l’état de l’objet (Requête)                                   |
|                          |                                                                                                        |
|                          |    - modifier l’état d’un objet sans retourner de résultat (Commande)                                  |
|                          |                                                                                                        |
|                          |  * Pour gérer les cas d’erreur et éviter d’utiliser « null » si un résultat n’est pas trouvé,          |
|                          |                                                                                                        |
|                          |    - utiliser le « Monade Result »                                                                     |
|                          |                                                                                                        |
|                          |      .. code-block:: csharp                                                                            |
|                          |                                                                                                        |
|                          |        Result result =  obj.Execute();                                                                 |
|                          |        Result<Employe> result = obj.GetEmployeById(id);                                                |
|                          |                                                                                                        |
+--------------------------+--------------------------------------------------------------------------------------------------------+
| - Gestion des erreurs    |  * Fail fast                                                                                           | 
| - Stabilité du code      |                                                                                                        |
|                          |    - Vérifier en début de fonction les paramètres d’entrée (Guard clause)                              |
|                          |                                                                                                        |
|                          |    - Si quelque chose risque de ne pas fonctionner en production,  faire en sorte que ça plante        |
|                          |      le plus vite possible ; idéalement,                                                               |
|                          |                                                                                                        |
|                          |      + que ça ne compile pas ou                                                                        |
|                          |                                                                                                        |
|                          |      + dès le démarrage de l’application avec un message d’erreur explicite                            |
|                          |        (exemple clé-valeur non présente dans app.config)                                               |
|                          |                                                                                                        |
|                          |  * Être en contrôle du cycle de vie des objets. Ex :                                                   |
|                          |                                                                                                        |
|                          |    - Utiliser using pour les connexions aux BD                                                         |
|                          |                                                                                                        |
|                          |  * Éviter l’utilisation des « null » (mettre des valeurs par défaut, …)                                |
+--------------------------+--------------------------------------------------------------------------------------------------------+
| - Commentaires           |                                                                                                        |
|                          | * Les commentaires présents sont utiles                                                                |
|                          |                                                                                                        |
|                          | * Les commentaires correspondent au code                                                               |
|                          |                                                                                                        |
|                          | * Pas de code en commentaire                                                                           |
|                          |                                                                                                        |
|                          | * Est-ce que ce commentaire a pour but de pallier à un problème de code sale ?                         |
|                          |   Pourquoi ne pas rendre propre le code sale ?                                                         |
|                          |                                                                                                        |
+--------------------------+--------------------------------------------------------------------------------------------------------+ 
| - Formatage              |                                                                                                        |
|                          | * La ligne doit être entièrement visible à l’écran                                                     |
|                          |                                                                                                        |
|                          | * De même qu’un article de journal présente le titre avant les détails, placer les méthodes publiques  |
|                          |   avant les méthodes privées                                                                           |
|                          |                                                                                                        |
|                          | * Les méthodes proches conceptuellement doivent être proches verticalement                             |
|                          |                                                                                                        |
+--------------------------+--------------------------------------------------------------------------------------------------------+ 


