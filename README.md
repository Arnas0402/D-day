<!DOCTYPE html>
<html>
<head>
    <title>D-Dienos GIS Žemėlapis</title>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    <style>
        #map { height: 600px; }
    </style>
</head>
<body>
    <h2>D-Dienos interaktyvus GIS žemėlapis</h2>
    <div id="map"></div>
    <script>
        var map = L.map('map').setView([49.4144, -0.8322], 8); // Normandija, Prancūzija

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; OpenStreetMap contributors'
        }).addTo(map);

        var locations = [
            { name: "Utah Beach", coords: [49.4144, -1.1783] },
            { name: "Omaha Beach", coords: [49.3670, -0.8770] },
            { name: "Gold Beach", coords: [49.3373, -0.4618] },
            { name: "Juno Beach", coords: [49.3300, -0.4083] },
            { name: "Sword Beach", coords: [49.2900, -0.2936] },
            { name: "Sainte-Mère-Église", coords: [49.4081, -1.3064] },
            { name: "Pegasus tiltas", coords: [49.2456, -0.2734] },
            { name: "Carentan", coords: [49.3035, -1.2485] },
            { name: "Bayeux", coords: [49.2767, -0.7033] },
            { name: "Caen", coords: [49.1830, -0.3700] }
        ];

        locations.forEach(function(location) {
            L.marker(location.coords).addTo(map)
                .bindPopup("<b>" + location.name + "</b>");
        });

        var alliedPath = L.polyline([
            [50.9097, -1.4043], // Southampton, UK
            [49.4144, -1.1783], // Utah Beach
            [49.3670, -0.8770], // Omaha Beach
            [49.3373, -0.4618], // Gold Beach
            [49.3300, -0.4083], // Juno Beach
            [49.2900, -0.2936]  // Sword Beach
        ], {color: 'blue'}).addTo(map);

        var germanDefense = L.polyline([
            [49.4144, -1.1783],
            [49.3670, -0.8770],
            [49.3373, -0.4618],
            [49.3300, -0.4083],
            [49.2900, -0.2936]
        ], {color: 'red', dashArray: '5,5'}).addTo(map);
    </script>
</body>
</html>
# D-day
