# Curs QGIS 3

15/05/2018

Victor Olaya @volaya

//wifi vcppjqn4

## API de QGIS

Recursos:
- https://qgis.org/api/
- https://docs.qgis.org/testing/en/docs/pyqgis_developer_cookbook/

Snippets:
- http://geoapis.sourcepole.com/
- https://webgeodatavore.github.io/pyqgis-samples/

Llibreria de commons: https://github.com/boundlessgeo/lib-qgis-commons/blob/master/qgiscommons2/gui/passwordlineedit.py

Veure tb https://github.com/volaya/curso-qgis-python/blob/master/enlaces.md


## Workshop


### Dia 1

1) Carreguem shape /home/gisce/projects/qgis-curs/curso-qgis-python/datos/.shp

2) Obrim consola python i mirem que és "iface"

```
iface
<qgis._gui.QgisInterface object at 0x7f6e1f0be288>

iface.activeLayer
<built-in method activeLayer of QgisInterface object at 0x7f6e1f0be288>

iface.activeLayer()
<qgis._core.QgsVectorLayer object at 0x7f6dbbf05a68>
```

Mirem a la api que és QgisInterface: https://qgis.org/api/classQgisInterface.html, ens interessem per activeLayer


3) Recuperem les features

```
list(iface.activeLayer().getFeatures())

[<qgis._core.QgsFeature object at 0x7f6dbbe9d558>, ..., <qgis._core.QgsFeature object at 0x7f6dc804a678>]


feature = list(iface.activeLayer().getFeatures())[0]

feature['wikipedia']
'afghanistan'

feature.geometry()
feature.geometry().asWkt()

'MultiPolygon (((61.21081709172574392 35.65007233330922531, 62.23065148300588589 35.27066396742229415, 62.98466230657660958 35.4040408391676209, 63.19353844590035152 35.85716563571891413, 63.98289594915870993 36.00795746514660323, 64.54647911973390251 36.31207326918426759, 64.74610517767740703 37.11181773533330386, 65.58894778835784223 37.30521678318564227, 65.74563073106682509 37.66116404881206847, 66.21738488145933843 37.39379018813392008, 66.51860680528866965 37.36278432875879218, 67.0757820982596229 37.35614390720928668, 67.82999962755951628 37.14499400486468517, 68.13556237170138274 37.0231151393043092, 68.85944583524593554 37.34433584243059556, 69.19627282092437781 37.15114350030742685, 69.51878543485796058 37.60899669041342008, 70.11657840361033323 37.58822276463209278, 70.27057417184013843 37.73516469985402466, 70.37630415230930225 38.13839590102752197, 70.8068205097328871 38.4862816432164152, 71.34813113799026496 38.2589053411321629, 71.23940392444816894 37.95326508234188623, 71.54191775908478235 37.90577444106564542, 71.44869347523024317 37.06564484308051988, 71.84463829945059388 36.73817129164692119, 72.19304080596239714 36.94828766534567421, 72.63688968291728543 37.04755809177835602, 73.26005577992501117 37.49525686293900151, 73.94869591664649988 37.42156627049079987, 74.980002475895418 37.41999013930589513, 75.15802778514091642 37.13303091078911677, 74.57589277537297789 37.02084137628345673, 74.06755171091782586 36.8361756454884528, 72.92002485544446699 36.72000702569631869, 71.84629194528392304 36.50994232842985809, 71.26234826038574965 36.07438751885780448, 71.49876793812109099 35.65056325941600335, 71.61307620635071203 35.15320343682286364, 71.1150187519216388 34.73312571872223486, 71.15677330921346311 34.34891144463215085, 70.88180301298839936 33.98885590263851952, 69.93054324735959426 34.02012014417510954, 70.32359419137159762 33.35853261975839246, 69.68714725126486087 33.10549896904123557, 69.26252200712255558 32.50194407808830022, 69.3177641132425606 31.90141225842444328, 68.92667687365766938 31.62018911389206721, 68.55693200060932213 31.71331004488201799, 67.79268924344478364 31.58293040620963055, 67.68339358914747095 31.30315420178142105, 66.93889122911846812 31.30491120047935283, 66.38145755398602432 30.73889923758645182, 66.34647260932442236 29.88794342703617701, 65.04686201361610642 29.4721806910319053, 64.35041873561851844 29.56003062592809272, 64.14800215033125141 29.34081920014597245, 63.55026085801117119 29.46833079682616585, 62.54985680527278191 29.31857249604431104, 60.8742484882087922 29.82923899995260797, 61.78122155136344418 30.73585032808123785, 61.69931440618083229 31.3795061304926719, 60.94194461451112943 31.54807465262875255, 60.86365481958896595 32.18291962333442768, 60.53607791529077531 32.98126882581156849, 60.9637003925060057 33.52883230237625867, 60.52842980331158174 33.67644603121800628, 60.80319339380744736 34.40410187431986344, 61.21081709172574392 35.65007233330922531)))'


```


```
layer = iface.activeLayer()
layer.fields()
<qgis._core.QgsFields object at 0x7f6dbbe9d5e8>
fields_list = layer.fields().toList()
fields_list
[<qgis._core.QgsField object at 0x7f6dbbe9d948>, <qgis._core.QgsField object at 0x7f6dbbe9d708>, <qgis._core.QgsField object at 0x7f6dbbe9d8b8>, <qgis._core.QgsField object at 0x7f6dbbe9d678>, <qgis._core.QgsField object at 0x7f6dbbe9d798>, <qgis._core.QgsField object at 0x7f6dc8040708>, <qgis._core.QgsField object at 0x7f6dc8040798>, <qgis._core.QgsField object at 0x7f6dc8040828>, <qgis._core.QgsField object at 0x7f6dc80408b8>, <q

fields_name = [f.name() for f in fields_list]
['scalerank', 'featurecla', 'LABELRANK', 'SOVEREIGNT', 'SOV_A3', 'ADM0_DIF', 'LEVEL', 'TYPE', 'ADMIN', 'ADM0_A3', 'GEOU_DIF', 'GEOUNIT', 'GU_A3', 'SU_DIF', 'SUBUNIT', 'SU_A3', 'BRK_DIFF', 'NAME', 'NAME_LONG', 'BRK_A3', 'BRK_NAME', 'BRK_GROUP', 'ABBREV', 'POSTAL', 'FORMAL_EN', 'FORMAL_FR', 'NAME_CIAWF', 'NOTE_ADM0', 'NOTE_BRK', 'NAME_SORT', 'NAME_ALT', 'MAPCOLOR7', 'MAPCOLOR8', 'MAPCOLOR9', 'MAPCOLOR13', 'POP_EST', 'POP_RANK', 'GDP_MD_EST', 'POP_YEAR', 'LASTCENSUS', 'GDP_YEAR', 'ECONOMY', 'INCOME_GRP', 'FIPS_10_', 'ISO_A2', 'ISO_A3', 'ISO_A3_EH', 'ISO_N3', 'UN_A3', 'WB_A2', 'WB_A3', 'WOE_ID', 'WOE_ID_EH', 'WOE_NOTE', 'ADM0_A3_IS', 'ADM0_A3_US', 'ADM0_A3_UN', 'ADM0_A3_WB', 'CONTINENT', 'REGION_UN', 'SUBREGION', 'REGION_WB', 'NAME_LEN', 'LONG_LEN', 'ABBREV_LEN', 'TINY', 'HOMEPART', 'MIN_ZOOM', 'MIN_LABEL', 'MAX_LABEL', 'wikipedia']


feature[fields_name[0]]
1
```



#### Exercici

Mirem els attributs de la capa (boto dreta sobre la capa "open attribute table")
camp "pop_est"

```
sum([feat['POP_EST'] for feat in list(iface.activeLayer().getFeatures())])
```

#### Com funcionen les cadenes d'expressió?

Com funcionen les cadenes d'expressió:
- "$COLUMN"
- 'STRING'

p.e "CONTINENT" == 'EUROPE'


#### Seguim investigant, getFeatures desde QGIS (sense iterar amb python)

https://qgis.org/api/classQgsVectorLayer.html

Té getFeatures()
https://qgis.org/api/classQgsVectorLayer.html#ae8351343cef4729c219a75e1d775aafa


KITKAT!


Per exemple, contarem la població de tots els paisos d'Europa

Python based filter
```
sum([f['POP_EST'] for f in iface.activeLayer().getFeatures() if f['CONTINENT'] in ["Europe"] ])
```

vs

CPP based filter //much more quick!
```
sum([f['POP_EST'] for f in iface.activeLayer().getFeatures('"CONTINENT" = \'Europe\'')])
```

#### Obrir capa vectorial en memòria per codi

La obrim en memòria, sense tindre-la a QGIS!
```
>>> layer = QgsVectorLayer("/home/gisce/projects/qgis-curs/curso-qgis-python/datos/ne_110m_admin_0_countries.shp", "capa")
```

I podem fer tot lo d'abans, getFeatures, ...



#### Obrir capa vectorial BUIDA en memòria per codi

Crearem una capa de punts amb tipus:"Point" i provider:"memory"
```
layer = QgsVectorLayer("Point?crs=EPSG:4326", "capa", "memory")

list(layer.getFeatures())
[]

list(layer.fields())
[]
```

La capa està buida com era d'esperar.

Crearem una sèrie de camps:
```
field = QgsField("id", QVariant.String)
layer.addAttribute(field)
False
```

Dona false perquè no hem obert la capa en mode edició, estirem directament del dataProvider de la capa


```
layer.dataProvider().addAttributes([field])
True

layer.updateFields()

list(layer.fields())
[<qgis._core.QgsField object at 0x7fd4dafc0c18>]
```


Afegim una feature
```
feature = QgsFeature()
layer.source()
'Point?crs=EPSG:4326&uid={5cadb660-043d-429f-b9bc-c1e968b8b518}'

# fields
feature.setFields(layer.fields())

# attributes
feature.setAttributes(["l"])

feature['id']
'l'

feature.setAttribute("id", "3")
feature['id']
'3
```

Afegim una geometria

//no cal actualitzar les geometries, només cal fer l'update pels camps
```
pt = QgsPointXY(1,1)
geom = QgsGeometry.fromPointXY(pt)
geom.asWkt()
'Point (1 1)'

feature.setGeometry(geom)
layer.dataProvider().addFeatures([feature])
(True, [<qgis._core.QgsFeature object at 0x7fd4dc640168>])
```

Agafem les features
```
list(layer.getFeatures())
[<qgis._core.QgsFeature object at 0x7fd4dc640048>]
```


#### Exercici, afegir n features amb punts dinàmics
```
from random import randint

HOW_MANY = 2
POINT_MIN = 0
POINT_MAX = 500

for _ in range(HOW_MANY):
    x = randint(POINT_MIN, POINT_MAX)
    y = randint(POINT_MIN, POINT_MAX)

    point = QgsPointXY(x,y)
    geom = QgsGeometry.fromPointXY(pt)

    feature.setGeometry(geom)
    layer.dataProvider().addFeatures([feature])
```


#### Projeccions

Sistemes de coordenades
```
layer.crs().authid()
'EPSG:4326'

epsg4325 = QgsCoordinateReferenceSystem("EPSG:4326")
epsg3857 = QgsCoordinateReferenceSystem("EPSG:3857")
transform = QgsCoordinateTransform(epsg4325, epsg3857, QgsProject.instance())

geom.transform(transform)

transform = QgsCoordinateTransform(epsg3857, epsg4325, QgsProject.instance())

geom.transform(transform)

geom.asWkt()
'Point (111319.49079327231447678 111325.14286638486373704)'

# i rollback
transform = QgsCoordinateTransform(epsg3857, epsg4325, QgsProject.instance())
geom.transform(transform)
0
geom.asWkt()
'Point (0.99999999999998868 0.99999999999998868)'
```


#### Calculadora de camps

Ens ajudarà a crear expressions complexes




-----------------------------



### Dia 2

#### Afegir accions

Dins de la config d'una layer, hi ha la opció "Sections"

Ens permetrà afegir una secció de tipus python.

Definirem l'scope (on apareix l'acció):
- "canvas" //l'afegeix a dins dels utils (icona settings)
- "feature scope" //ho tindrem dins de la vista del camp

Definim el codi en python:

```
[%wikipedia%]
```
, expressió que substitueix pel camp wikipedia

```
import urllib
import webbrowser

url ="https://en.wikipedia.org/wiki" + "[%wikipedia%]"

try:
	urllib.request.urlopen(url)
	webbrowser.open(url, new=0, autoraise=True)
except:
	QtGui.QMessageBox.warning(None, "asdadasd")
```

A la icona de settings apareixerà la nostra nova acció "wikipedia"


#### Map tips

Els tips permeten extendre els helpers i els títols d'ajudes relatius als elements mapa (per quan deixes el cursor a sobre durant un rato, com un title d'html).

Per tunejar-ho cal anar a la config d'una layer, secció "Display".

Activar els tips via menú "View" -> "Map tips".

Activem els maps tips, i seleccionem "wikipedia" dins del combo "Display expression".

Al deixar el cursor sobre un país ens apareix el nom del país!
