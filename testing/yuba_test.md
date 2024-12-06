---
jupyter:
  jupytext:
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.16.4
  kernelspec:
    display_name: spatial
    language: python
    name: python3
---

# Yuba Structures

```python
import geemap
import ee

```

```python
Map = geemap.Map(center=(40, -100), zoom=4)
Map
```

```python
yuba = ee.FeatureCollection("TIGER/2018/Counties").filter(ee.Filter.eq('NAME', 'Yuba'))
yuba_styled = yuba.style(**{"color": 'red', "fillColor": '#00000000'})
Map.addLayer(yuba_styled, {}, 'Yuba County')
Map
```

```python
Map.setCenter(-121.1821, 39.4154, 10)
```

```python
structure = 'D:/OneDrive/Documents/ArcGIS/Projects/2_Yuba_water/Suitability_map3_3.tif'
```

```python
Map.add_raster(structure, colormap="RdYlGn", layer_name="structures")
yuba = ee.FeatureCollection("TIGER/2018/Counties").filter(ee.Filter.eq('NAME', 'Yuba'))
yuba_styled = yuba.style(**{"color": 'black', "fillColor": '#00000000'})
Map.addLayer(yuba_styled, {}, 'Yuba County')
Map
```
