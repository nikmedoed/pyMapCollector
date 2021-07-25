# pythonUnversalMapCollector
Save map to big PNG from any cartographic resource (Yandex.maps, Google Maps etc).

Script automatically moves around the specified area of the map, takes screenshots of small areas and combines them into a large picture.

[TOC]

## Parameters
You should set:

- `INIT_LINK` - a link to the desired point with the selected scale.
- `SCREENSHOOT_WIDTH`, `SCREENSHOOT_HEIGHT` - size of the final image.
- `SCREENSHOOT_self_boundSize` - save zone for screenshoot. Different services have different safe zones. This depends on the size of the browser window and the location of the map controls.

Example:
```
INIT_LINK = "https://yandex.ru/maps/213/moscow/?ll=37.624027%2C55.753747&z=15.68"

SCREENSHOOT_WIDTH = 30000
SCREENSHOOT_HEIGHT = 45000

SCREENSHOOT_self_boundSize = 500
```

The collector is wrapped in a class `MapCollector`

```
MapCollector(
    INIT_LINK,  
    SCREENSHOOT_WIDTH, 
    SCREENSHOOT_HEIGHT, 
    SCREENSHOOT_self_boundSize,
    pointIsCenter=True, # point in link center or upper left corner
    sidebar=SIDEBAR
)
```

`sidebar` - a dictionary with lists of element classes to "close" before collecting

## Dependencies
- selenium
- PIL
- io
- tqdm

Also you need `Chrome` and actual version [`Selenium Chrome Driver`](https://chromedriver.chromium.org/downloads)
But you can redo the script for your favorite browser.

## Speed
The map of `30 000` by `45 000` pixels was collected for `2 hours and 35 minutes`.
The final `PNG` weighs `405 MB`.

![](dev/example.jpg)

## Bonus
`cutForPrint.py` - a script for cutting a large image into small ones for printing on paper.
You should to calculate how many pieces you need to cut a map.

###### ! Note 
Epson XP-342 has a print area `20.42 cm` by `28.89 cm` on `A4` . At `300 ppi`, this is `2412 px` by `3412 px`. I do not recommend printing without margins, because you will lose part of the image and will not be able to join the parts.

*My map for tracking cycling trips*
![](dev/mymap.jpg)