.. |RED| image:: /img/red.png
   :height: 11
   :width: 11
.. |GREEN| image:: /img/green.png
   :height: 11
   :width: 11
.. |CHECK| image:: /img/Check-icon3.png
   :height: 11
   :width: 11


+---------+--------------------------+--------------------------------------------+----------------------------------------------------+
|         |  Principe                |  |RED| Pas bien                            | |GREEN| Bien                                       |
+---------+--------------------------+--------------------------------------------+----------------------------------------------------+
|         |                          | .. code-block:: csharp                     | .. code-block:: csharp                             |
|         |                          |                                            |                                                    |
| |CHECK| |  Des noms prononçables   |     class DtaRcrd102{                      |     class Customer{                                |
|         |                          |       private DateTime genymdhms;          |       private DateTime generationTimestamp;        |
|         |                          |       private DateTime modymdhms;          |       private DateTime modificationTimestamp;      |
|         |                          |       private String pszqint = "102";      |       private String recordId = "102";             |
|         |                          |       /* ... */                            |        /* ... */                                   |
|         |                          |     };                                     |     };                                             |
|         |                          |                                            |                                                    |
+---------+--------------------------+--------------------------------------------+----------------------------------------------------+
|         |                          | .. code-block:: csharp                     | .. code-block:: csharp                             |
|         |                          |                                            |                                                    |
| |CHECK| | Utiliser des constantes  |     class DtaRcrd102{                      |     class Customer{                                |
|         |                          |       private DateTime genymdhms;          |       private DateTime generationTimestamp;        |
|         |                          |       private DateTime modymdhms;          |       private DateTime modificationTimestamp;      |
|         |                          |       private String pszqint = "102";      |       private String recordId = "102";             |
|         |                          |       /* ... */                            |        /* ... */                                   |
|         |                          |     };                                     |     };                                             |
|         |                          |                                            |                                                    |
+---------+--------------------------+--------------------------------------------+----------------------------------------------------+
|         |                          | .. code-block:: csharp                     | .. code-block:: csharp                             |
|         |                          |                                            |                                                    |
| |CHECK| | Éviter les effets de     |     class DtaRcrd102{                      |     class Customer{                                |
|         | bords.                   |       private DateTime genymdhms;          |       private DateTime generationTimestamp;        |
|         | Pas bien à cause de      |       private DateTime modymdhms;          |       private DateTime modificationTimestamp;      |
|         | Session.initialize       |       private String pszqint = "102";      |       private String recordId = "102";             |
|         |                          |       /* ... */                            |        /* ... */                                   |
|         |                          |     };                                     |     };                                             |
|         |                          |                                            |                                                    |
+---------+--------------------------+--------------------------------------------+----------------------------------------------------+
