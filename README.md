osmapi
======

Python wrapper for the OSM API

## Installation

Install `osmapi` simply by using pip:

    pip install osmapi

### Development

If you want to help with the development of `osmapi`, you should clone this repository and install the requirements:

    pip install -r pip-requirements.txt

After that, it is recommended to install the `flake8` pre-commit-hook:

    flake8 --install-hook

## Note

Scripted imports and automated edits should only be carried out by those with experience and understanding of the way the OpenStreetMap community creates maps, and only with careful **planning** and **consultation** with the local community.

See the [Import/Guidelines](http://wiki.openstreetmap.org/wiki/Import/Guidelines) and [Automated Edits/Code of Conduct](http://wiki.openstreetmap.org/wiki/Automated_Edits/Code_of_Conduct) for more information.

## Examples

### Read from OpenStreetMap

```python
import osmapi.OsmApi
MyApi = OsmApi.OsmApi()
print MyApi.NodeGet(123)
# {u'changeset': 532907, u'uid': 14298,
# u'timestamp': u'2007-09-29T09:19:17Z',
# u'lon': 10.790009299999999, u'visible': True,
# u'version': 1, u'user': u'Mede',
# u'lat': 59.9503044, u'tag': {}, u'id': 123}
```

### Constructor

```python
import osmapi.OsmApi
MyApi = OsmApi.OsmApi(api="api06.dev.openstreetmap.org", username = "you", password = "***")
MyApi = OsmApi.OsmApi(username = "you", passwordfile = "/etc/mypasswords")
MyApi = OsmApi.OsmApi(passwordfile = "/etc/mypasswords") # username will be first line username
```

Note: The password file should have the format _user:password_

### Write to OpenStreetMap

```python
import osmapi.OsmApi
MyApi = OsmApi.OsmApi(username = u"metaodi", password = u"*******")
MyApi.ChangesetCreate({u"comment": u"My first test"})
print MyApi.NodeCreate({u"lon":1, u"lat":1, u"tag": {}})
# {u'changeset': 532907, u'lon': 1, u'version': 1, u'lat': 1, u'tag': {}, u'id': 164684}
MyApi.ChangesetClose()
```

## Attribution

This project was orginally developed by Etienne Chové.
This repository is a copy of the original code from SVN (http://svn.openstreetmap.org/applications/utils/python_lib/OsmApi/OsmApi.py), with the goal to enable easy contribution via GitHub and release of this package via [PyPI](https://pypi.python.org/pypi/osmapi).

See also the OSM wiki: http://wiki.openstreetmap.org/wiki/PythonOsmApi
