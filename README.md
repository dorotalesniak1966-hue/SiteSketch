<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8" />
<title>SiteSketch</title>

<link rel="stylesheet" href="https://unpkg.com/leaflet/dist/leaflet.css" />
<link rel="stylesheet" href="https://unpkg.com/leaflet-draw/dist/leaflet.draw.css"/>

<style>
body { margin:0; }
#map { height:100vh; }
</style>
</head>

<body>

<div id="map"></div>

<script src="https://unpkg.com/leaflet/dist/leaflet.js"></script>
<script src="https://unpkg.com/leaflet-draw/dist/leaflet.draw.js"></script>

<script>

var map = L.map('map').setView([52.237, 21.017], 13);

L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
maxZoom: 19
}).addTo(map);

var drawnItems = new L.FeatureGroup();
map.addLayer(drawnItems);

var drawControl = new L.Control.Draw({
edit: { featureGroup: drawnItems },
draw: {
polygon: false,
circle: false,
rectangle: false
}
});

map.addControl(drawControl);

map.on(L.Draw.Event.CREATED, function (e) {
var layer = e.layer;
drawnItems.addLayer(layer);
});

</script>

</body>
</html>
