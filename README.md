# mta_python_webide_killer
Multi-Target Application with a Python module that will not work when imported into WebIDE

[https://github.com/alundesap/mta_python_webide_killer.git](https://github.com/alundesap/mta_python_webide_killer.git)

Get python dependencies

```
cd srv/python
pip download -d vendor -r requirements.txt --find-links ../../../sap_dependencies --find-links ../../../hana_ml-1.0.3.tar.gz hana_ml
```
 

Manually build the python module

```
git pull
xs push webide-killer.python -k 1024M -m 256M -n python -p srv/python --no-start
xs start webide-killer.python

git pull ; xs push webide-killer.python -k 1024M -m 256M -n python -p srv/python
```

When attempting a top-level project build (MTAR build) the following occurs when the python module definition is uncommented.
```
11:38:08 AM (Builder) Build of "/mta_python_webide_killer" started.
11:38:14 AM (DIBuild) [INFO] Target platform is XSA[INFO] Reading mta.yaml[INFO] Processing mta.yaml[INFO] Processing module app[INFO] Processing module python[INFO] Processing module node[ERROR] Module python does not exist in the folder srv/python.
11:38:14 AM (Builder) Build of /mta_python_webide_killer failed.
```

Within the MTA.YAML file python module properties don't work.
```
# If this section is uncommented, the app module will not run due to missing reference.
### Python Requires Block Begin vvv
#    - name: python_api
#      group: destinations
#      properties:
#        name: python_be
#        url: ~{url}
#        forwardAuthToken: true
### Python Requires Block End ^^^
```


