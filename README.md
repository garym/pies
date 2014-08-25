# PIES

PIES (PlugIn Extension System) is a very simple plugin framework based on the
code from [A Simple Plugin Framework][1] posted in 2008 by Marty Alchin.

It may be rare for 6 lines of functional code to require their own separate
source repository, the maintainer of this code has used the code in more than
one project now.

The main difference between Marty's work and the code in this repository is in
the documentation which is targetted at Python 3 use.

## Installation

There are no dependencies
```sh
python setup.py install
```

## Usage

### Specifying a mount point:

```py
from pies import PluginMount

class EventProvider(metaclass=PluginMount):
    """mount point for events"""
```

### Creating a plugin:

Any class that inherits the mount point is a plugin

```
class AnEvent(EventProvider):
    """an implementation of an EventProvider"""
    def __init__(self):
        print("initialised")

    def process(self):
        """do something useful"""
```

### Using your plugin:

```py
events = EventProvider.get_plugins()
[e.process() for e in events]
```

[1]: http://martyalchin.com/2008/jan/10/simple-plugin-framework/

