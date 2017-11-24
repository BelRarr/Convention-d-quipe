
+-------------------------+------------------------------------------+--------------------------------------------------------+
| Principe                |  Bien                                    |  Pas bien                                              |
+-------------------------+------------------------------------------+--------------------------------------------------------+
| Des noms prononçables   | .. code-block:: ruby                     | - 1                                                    |
|                         |    class DtaRcrd102{                     | - 2                                                    |
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

    # TextFSM template...
    TEMPLATE = """Value INTF (\S+)\nValue IPADDR (\S+)\nValue STATUS (up|down|administratively down)\nValue PROTO (up|down)\n\nStart\n  ^${INTF}\s+${IPADDR}\s+\w+\s+\w+\s+${STATUS}\s+${PROTO} -> Record"""

    # Interfaces() is used to map TextFSM template values to the TOML Log
    class Interfaces(TraitTable):
        intf = CUnicode()  # See the traitlets documentation for CUnicode usage
        addr = CUnicode()
        status = CUnicode()
        # Usage of CUnicodeRegex illustrated below... it errors if no match
        proto = CUnicodeRegex(r'down|up')
        _map = ('intf', 'addr', 'status', 'proto') # TextFSM field order

    # Create a log named rviews_intfs, which automatically rotates at midnight
    #     category must be unique per logging file
    log = RotatingTOMLLog('rviews_intfs', category='route-views')

    ## Define a tuple of username and password pairs here...
    ##    The first is an expected failure to illustrate how it works
    accts = (Account('itsa-mistake', ''), Account('rviews', 'secret2'),)

    ## You can optionally disable auto-enable mode if you like...
    conn = CLIMachine('route-views.routeviews.org', accts,
        auto_priv_mode=False, log_screen=True, debug=False, command_timeout=5)

    conn.execute('term len 0', wait=0.5)    # Wait 0.5 seconds after the cmd
    conn.execute('show version', regex='test>') # regex is another prompt string

    conn.execute('show users', timeout=60)  # 'show users' outputs slowly...
    ## Get the result of the 'show users' command...
    user_output = conn.response

    ## Automatically parse with TextFSM and log to a TOML log
    for ii in range(0, 5):
        intf_list = conn.execute('show ip int brief', template=TEMPLATE)
        for vals in intf_list:
            ## NOTE: info must be a dictionary to be parsed by .write_table_list()
            info = dict(Interfaces(vals))  # <---- This is the info table
            ## Write a timestamped list of tables named 'rview_intf' to the log
            log.write_table_list(table='rview_intf', info=info, timestamp=True)
        time.sleep(1)

    conn.logout()


Installation
------------
