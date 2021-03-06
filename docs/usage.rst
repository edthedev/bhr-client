Usage
=====

First, export the ``BHR_TOKEN`` and ``BHR_HOST`` environment variables::

    $ export BHR_TOKEN=abc91639287637189236193671983619783619c4
    $ export BHR_HOST=http://localhost:8000

Then, you can create a :class:`bhr_client.rest.Client` object::

    $ python
    >>> from bhr_client.rest import login_from_env
    >>> c = login_from_env()
    >>> c.stats()
    {u'current': 3650, u'expected': 3606, u'block_pending': 1, u'unblock_pending': 45}
    >>> c.query("192.168.254.254")
    []
    >>> c.block(cidr='192.168.254.254', source='readme', why='because!', duration=300)
    {u'added': u'2014-11-14T15:30:24.785Z',
     u'cidr': u'192.168.254.254/32',
     u'set_blocked': u'http://localhost:8000/bhr/api/blocks/359147/set_blocked/',
     u'skip_whitelist': False,
     u'source': u'readme',
     u'unblock_at': u'2014-11-14T15:35:24.784Z',
     u'url': u'http://localhost:8000/bhr/api/blocks/359147/',
     u'who': u'admin',
     u'why': u'because!'}
    >>> c.query("192.168.254.254")
    [{u'added': u'2014-11-14T15:30:24.785Z',
      u'cidr': u'192.168.254.254/32',
      u'set_blocked': u'http://localhost:8000/bhr/api/blocks/359147/set_blocked/',
      u'skip_whitelist': False,
      u'source': u'readme',
      u'unblock_at': u'2014-11-14T15:35:24.784Z',
      u'url': u'http://localhost:8000/bhr/api/blocks/359147/',
      u'who': u'admin',
      u'why': u'because!'}]

Instead of using :func:`bhr_client.rest.login_from_env` you can use 
:func:`bhr_client.rest.login` explicitly.
