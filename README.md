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
