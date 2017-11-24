
+-------------------------+------------------------------------------+--------------------------------------------------------+
| Principe                |  ![#f03c15]() Bien                       |  Pas bien                                              |
+-------------------------+------------------------------------------+--------------------------------------------------------+
| Des noms prononçables   | .. code-block:: csharp                   | - 1                                                    |
|                         |                                          | - 1                                                    |
|                         |     class DtaRcrd102{                    | - 2                                                    |
+-------------------------+------------------------------------------+--------------------------------------------------------+


```python
import this
```

Essentially, this is a simple wrapper around pexpect_. Standard usage:

.. code:: python

    import time

    from clijockey.traits import TraitTable, CUnicode, CUnicodeRegex
    from clijockey.traits import CMacAddressCisco, CIPv4AddressStr
    from clijockey.util import RotatingTOMLLog
    from clijockey.util import Account
    from clijockey.lib import CLIMachine


    conn.logout()
