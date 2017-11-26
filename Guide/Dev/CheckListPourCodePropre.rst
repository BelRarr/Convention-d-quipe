.. |RED| image:: /img/red.png
   :height: 11
   :width: 11
.. |GREEN| image:: /img/green.png
   :height: 11
   :width: 11
.. |CHECK| image:: /img/Check-icon4.png
   :height: 11
   :width: 11


+---------+-------------------------+----------------------------------------+---------------------------------------------------------+
|         |  Principe               |  |RED| Pas bien                        | |GREEN| Bien                                            |
+---------+-------------------------+----------------------------------------+---------------------------------------------------------+
|         |                         | .. code-block:: csharp                 | .. code-block:: csharp                                  |
|         |                         |                                        |                                                         |
| |CHECK| |  Des noms prononçables  |   class DtaRcrd102{                    |  class Customer{                                        |
|         |                         |     private DateTime genymdhms;        |    private DateTime generationTimestamp;                |
|         |                         |     private DateTime modymdhms;        |    private DateTime modificationTimestamp;              |
|         |                         |     private String pszqint = "102";    |    private String recordId = "102";                     |
|         |                         |     /* ... */                          |     /* ... */                                           |
|         |                         |   };                                   |  };                                                     |
|         |                         |                                        |                                                         |
+---------+-------------------------+----------------------------------------+---------------------------------------------------------+
|         |                         | .. code-block:: csharp                 | .. code-block:: csharp                                  |
|         |                         |                                        |                                                         |
| |CHECK| | Utiliser des constantes |   int s = 0;                           |  int realDaysPerIdealDay = 4;                           |
|         |                         |   for (int j = 0; j < 34; j++){        |  const int WORK_DAYS_PER_WEEK = 5;                      | 
|         |                         |     s += (t[j] * 4) / 5;               |  int sum = 0;                                           |
|         |                         |   }                                    |  for (int j = 0; j < NUMBER_OF_TASKS; j++){             |
|         |                         |                                        |    int realTaskDays = taskEstimate[j] *                 |
|         |                         |                                        |                       realDaysPerIdealDay;              |
|         |                         |                                        |    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK); |
|         |                         |                                        |    sum += realTaskWeeks;                                |
|         |                         |                                        |  }                                                      |
+---------+-------------------------+----------------------------------------+---------------------------------------------------------+
|         |                         | .. code-block:: csharp                 | .. code-block:: csharp                                  |
|         |                         |                                        |                                                         |
| |CHECK| | Éviter les effets de    |   public Boolean checkPassword(        |    public Boolean checkPassword(                        |
|         | bords.                  |     String userName, String password){ |      String userName, String password){                 |
|         | Pas bien à cause de     |      User user =                       |       User user =                                       |
|         | Session.initialize      |       UserGateway.findByName(userName);|        UserGateway.findByName(userName);                |
|         |                         |      if (user != null) {               |       if (user != null) {                               |
|         |                         |         /* ... */                      |          /* ... */                                      |
|         |                         |         Session.initialize();          |          return true;                                   |
|         |                         |         return true;                   |      };                                                 |
|         |                         |      };                                |      return false;                                      |
|         |                         |      return false;                     |    }                                                    |
|         |                         |   }                                    |                                                         |
+---------+-------------------------+----------------------------------------+---------------------------------------------------------+
|         |                         | .. code-block:: csharp                 | .. code-block:: csharp                                  |
|         |                         |                                        |                                                         |
| |CHECK| | Mettre du contexte      |     class DtaRcrd102{                  |     class Customer{                                     |
|         | pertinent               |       private DateTime genymdhms;      |       private DateTime generationTimestamp;             |
|         |                         |       private DateTime modymdhms;      |       private DateTime modificationTimestamp;           |
|         |                         |       private String pszqint = "102";  |       private String recordId = "102";                  |
|         |                         |       /* ... */                        |        /* ... */                                        |
|         |                         |     };                                 |     };                                                  |
|         |                         |                                        |                                                         |
+---------+-------------------------+----------------------------------------+---------------------------------------------------------+
