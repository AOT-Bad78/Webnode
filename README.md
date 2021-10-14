
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css" integrity="sha512-xodZBNTC5n17Xt2atTPuE1HxjVMSvLVW9ocqUKLsCC5CXdbqCmblAshOMAS6/keqq/sMZMZ19scR4PsZChSR7A==" crossorigin="">
  
  <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js" integrity="sha512-XQoYMqMTK8LvdxXYG3nZ448hOEQiglfqkJs1NOQV44cWnUrBc8PkAOcXy20w0vlaXaVUearIOBhiXZ5V3ynxwA==" crossorigin=""></script>
	<script type="text/javascript" src="https://cdnnen.proxi.tools/res/global/js/leaflet/Leaflet.Control.Custom.js"></script>
<style>

.location-infobox {
    background: #fff;
    border-radius: 2px;
    padding: 9px 11px;
    box-shadow: rgba(0, 0, 0, 0.3) 0px 1px 4px -1px;
    font-family: Roboto, Arial, sans-serif;
    font-size: 12px;
	text-align: left;
    line-height: 16px;
    color: #5B5B5B;
    width: 100%;
}
.location-infobox .placecard__container {
    display: grid;
    grid-template-columns: 3fr 1fr;
}

.location-infobox .placecard__business-name {
    font-weight: bold;
	text-align: left;
    font-size: 14px;
    line-height: 17px;
    color: #000;
    margin-bottom: 5px;
}

</style>

 	
<div id="map" style="width: 490px; height: 600px;"></div>
<script>
	let map = null;
	let placecard = "\n                   <div class=\"placecard__left\">\n                <p class=\"placecard__business-name\">Créneaux d'entraînement<\p>\n  Mercredi : 20h00 / 22h00 - Gymnase Broustal     <br/>  Vendredi : 20h00 / 22h00 - Gymnase Rousseau <br/>           Samedi : 09h30 / 12h00 - Gymnase Gagarine<br>\n             <\p>\n            ";
  
	let zoom = 15;
	let mapType = false;
        let scale = false;
	   function initMap() {
            
                            
                map = L.map('map', {
                    center: [48.78091491800281, 1.9872312511900436],
                    zoom: zoom,
                    zoomControl: false,
                    gestureHandling: true,
                    attributionControl: '<a href="https://cartodream.wixsite.com/website-1">Cartodream</a> , <a href="https://www.openstreetmap.fr/">OSM</a>'
                });

		var LeafIcon = L.Icon.extend({
		options: {
			iconSize:     [80, 80],
		}
	});
	L.tileLayer('http://{s}.tile.openstreetmap.fr/osmfr/{z}/{x}/{y}.png', {
		attribution: '<a href="https://cartodream.wixsite.com/website-1">Cartodream</a> , <a href="https://www.openstreetmap.fr/">OSM</a>',
	
	}).addTo(map);
	
        var BroustalIcon = new LeafIcon({iconUrl: 'https://aot-badminton-draft.webnode.fr/_files/200000675-8142c8142e/Volant_BROUSTAL.png'}); 
	var RousseauIcon = new LeafIcon({iconUrl: 'https://aot-badminton-draft.webnode.fr/_files/200000677-0d0100d013/Volant_ROUSSEAU.png'});
	var GagarineIcon = new LeafIcon({iconUrl: 'https://aot-badminton-draft.webnode.fr/_files/200000676-6665b6665e/Volant_GAGARINE.png'});               
	
	L.marker([48.78275817457628, 1.9787277927155338],{icon: BroustalIcon}).addTo(map)
			.bindPopup("<b>Gymnase Anne-Marie et André Broustal</b><br/>6 Avenue Ludwig Van Beethoven 78190 Trappes<br /><b><img src='https://aot-badminton.fr/_files/200000272-b5bd2b6b4e/Broustal.PNG' target='_blank' width='100%' height='100%'/></b><br /><a href=\"https:\/\/maps.google.com\/maps\/dir\/\/Gymnase Broustal 78190 Trappes\" target=\"_blank\"><b>Itinéraire</b></a>")

	L.marker([48.776327111701995, 1.9959440828648392],{icon: RousseauIcon}).addTo(map)
			.bindPopup("<b>Gymnase Rousseau</b><br/>2 rue Alfred Costes 78190 Trappes<br /><b><img src='https://aot-badminton.fr/_files/200000271-f0308f12a6/Rousseau%20Trappes.PNG' target='_blank' width='100%' height='100%'/></b><br /><a href=\"https:\/\/maps.google.com\/maps\/dir\/\/2 Rue Alfred Costes 78190 Trappes\" target=\"_blank\"><b>Itinéraire</b></a>")	

	L.marker([48.77606004609193, 1.9796608345104458],{icon: GagarineIcon}).addTo(map)
			.bindPopup("<b>Gymnase Gagarine</b><br/>4 Rue Pierre Courtade 78190 Trappes<br /><b><img src='https://aot-badminton-draft.webnode.fr/_files/200000669-23a7b23a7d/Gargarine%20Trappes.JPG' target='_blank' width='100%' height='100%'/></b><br /><a href=\"https:\/\/maps.google.com\/maps\/dir\/\/Complexe Sportif Youri Gagarine 78190 Trappes\" target=\"_blank\"><b>Itinéraire</b></a>");

	    if(scale) {
                    L.control.scale({
                        position: 'bottomright',
                        imperial: false
                    }).addTo(map);
                }
                L.control.zoom({
                    position: 'bottomright',
                }).addTo(map);
                
                                    
                    L.control.custom({
                        position: 'topleft',
                        content: placecard,
                        classes: 'location-infobox',
                        /*
                        style: {
                            width: '200px',
                            margin: '10px',
                            padding: '5px 10px',
                            background: '#fff',
                        },
                         */
                    }).addTo(map);
                    
                                        
        }
        

                    window.onload = function(){
                initMap();
            };
</script>
