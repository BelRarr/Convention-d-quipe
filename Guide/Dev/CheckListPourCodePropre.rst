.. |RED| image:: /img/red.png
   :height: 11
   :width: 11
.. |GREEN| image:: /img/green.png
   :height: 11
   :width: 11
.. |CHECK| image:: /img/Check-icon3.png
   :height: 11
   :width: 11


+---------+--------------------------+--------------------------------------------+------------------------------------------------------+
|         |  Principe                |  |RED| Pas bien                            | |GREEN| Bien                                         |
+---------+--------------------------+--------------------------------------------+------------------------------------------------------+
|         |                          | .. code-block:: csharp                     | .. code-block:: csharp                               |
|         |                          |                                            |                                                      |
| |CHECK| |  Des noms prononçables   |     class DtaRcrd102{                      |     class Customer{                                  |
|         |                          |       private DateTime genymdhms;          |       private DateTime generationTimestamp;          |
|         |                          |       private DateTime modymdhms;          |       private DateTime modificationTimestamp;        |
|         |                          |       private String pszqint = "102";      |       private String recordId = "102";               |
|         |                          |       /* ... */                            |        /* ... */                                     |
|         |                          |     };                                     |     };                                               |
|         |                          |                                            |                                                      |
+---------+--------------------------+--------------------------------------------+------------------------------------------------------+

