.. |RED| image:: /img/red.png
   :height: 11
   :width: 11
.. |GREEN| image:: /img/green.png
   :height: 11
   :width: 11
.. |CHECK| image:: /img/Check-icon4.png
   :height: 11
   :width: 11


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

