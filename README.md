This shows an implementation of indy256's Convexhull.js for Leaflet L.latLng points. 




```javascript
function showConvexHull() {  
    var pointsArray = createPointsArray();
    pointsArray.forEach(function(element) { L.marker(element).addTo(mymap)});
    var points = pointsArray.map(function (element) {
        return {
            x: element.lat,
            y: element.lng
            }
        }
    )
    var convexHullPoints = convexHull(points);
    var newStuff = convexHullPoints.map(function (element) {return ([element.x,element.y])})
    var convexHullPolygon = L.polygon(newStuff, ).addTo(mymap);
    
    var bounds = convexHullPolygon.getBounds();
    mymap.fitBounds(bounds);

}


//create L.latLng objects
function createLatLngArray() {
    var latlngArray = [];
    latlngArray.push(L.latLng(50.5, 30.5))
    latlngArray.push(L.latLng(51.5, 31.5))
    latlngArray.push(L.latLng(51.5, 32.5))
    latlngArray.push(L.latLng(50.7, 30.7))
    latlngArray.push(L.latLng(50.8, 30.6))
    latlngArray.push(L.latLng(51.5, 33.5))
    latlngArray.push(L.latLng(53, 32.3))
    latlngArray.push(L.latLng(51.7, 30.2))
    
    return latlngArray;          
}

```




