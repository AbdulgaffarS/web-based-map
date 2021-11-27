<!doctype html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="initial-scale=1,user-scalable=no,maximum-scale=1,width=device-width">
        <meta name="mobile-web-app-capable" content="yes">
        <meta name="apple-mobile-web-app-capable" content="yes">
        <link rel="stylesheet" href="css/leaflet.css"><link rel="stylesheet" href="css/L.Control.Locate.min.css">
        <link rel="stylesheet" href="css/qgis2web.css"><link rel="stylesheet" href="css/fontawesome-all.min.css">
        <link rel="stylesheet" href="css/leaflet-search.css">
        <link rel="stylesheet" href="css/leaflet-control-geocoder.Geocoder.css">
        <link rel="stylesheet" href="css/leaflet-measure.css">
        <style>
        #map {
            width: 1066px;
            height: 579px;
        }
        </style>
        <title></title>
    </head>
    <body>
        <div id="map">
        </div>
        <script src="js/qgis2web_expressions.js"></script>
        <script src="js/leaflet.js"></script><script src="js/L.Control.Locate.min.js"></script>
        <script src="js/multi-style-layer.js"></script>
        <script src="js/leaflet-svg-shape-markers.min.js"></script>
        <script src="js/leaflet.rotatedMarker.js"></script>
        <script src="js/leaflet.pattern.js"></script>
        <script src="js/leaflet-hash.js"></script>
        <script src="js/Autolinker.min.js"></script>
        <script src="js/rbush.min.js"></script>
        <script src="js/labelgun.min.js"></script>
        <script src="js/labels.js"></script>
        <script src="js/leaflet-control-geocoder.Geocoder.js"></script>
        <script src="js/leaflet-measure.js"></script>
        <script src="js/leaflet-search.js"></script>
        <script src="data/Administative_0.js"></script>
        <script src="data/Boundary_1.js"></script>
        <script src="data/Banks_2.js"></script>
        <script src="data/FillingStation_3.js"></script>
        <script src="data/Healthfacilities_4.js"></script>
        <script src="data/Hotels_5.js"></script>
        <script src="data/Others_6.js"></script>
        <script src="data/Recreational_centres_7.js"></script>
        <script src="data/Restaurant_8.js"></script>
        <script src="data/Schools_9.js"></script>
        <script src="data/Roundabouts_10.js"></script>
        <script src="data/Majorroads_11.js"></script>
        <script src="data/Railway_12.js"></script>
        <script src="data/Streets_13.js"></script>
        <script src="data/Minorroads_14.js"></script>
        <script>
        var highlightLayer;
        function highlightFeature(e) {
            highlightLayer = e.target;

            if (e.target.feature.geometry.type === 'LineString') {
              highlightLayer.setStyle({
                color: '#ffff00',
              });
            } else {
              highlightLayer.setStyle({
                fillColor: '#ffff00',
                fillOpacity: 1
              });
            }
        }
        var map = L.map('map', {
            zoomControl:true, maxZoom:28, minZoom:1
        })
        var hash = new L.Hash(map);
        map.attributionControl.setPrefix('<a href="https://github.com/tomchadwin/qgis2web" target="_blank">qgis2web</a> &middot; <a href="https://leafletjs.com" title="A JS library for interactive maps">Leaflet</a> &middot; <a href="https://qgis.org">QGIS</a>');
        var autolinker = new Autolinker({truncate: {length: 30, location: 'smart'}});
        L.control.locate({locateOptions: {maxZoom: 19}}).addTo(map);
        var measureControl = new L.Control.Measure({
            position: 'topleft',
            primaryLengthUnit: 'meters',
            secondaryLengthUnit: 'kilometers',
            primaryAreaUnit: 'sqmeters',
            secondaryAreaUnit: 'hectares'
        });
        measureControl.addTo(map);
        document.getElementsByClassName('leaflet-control-measure-toggle')[0]
        .innerHTML = '';
        document.getElementsByClassName('leaflet-control-measure-toggle')[0]
        .className += ' fas fa-ruler';
        var bounds_group = new L.featureGroup([]);
        function setBounds() {
            if (bounds_group.getLayers().length) {
                map.fitBounds(bounds_group.getBounds());
            }
        }
        function pop_Administative_0(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Administative_Blds'] !== null ? autolinker.link(feature.properties['Administative_Blds'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Administative_0_0() {
            return {
                pane: 'pane_Administative_0',
                radius: 4.0,
                opacity: 1,
                color: 'rgba(61,128,53,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 2.0,
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(161,169,176,1.0)',
                interactive: true,
            }
        }
        map.createPane('pane_Administative_0');
        map.getPane('pane_Administative_0').style.zIndex = 400;
        map.getPane('pane_Administative_0').style['mix-blend-mode'] = 'normal';
        var layer_Administative_0 = new L.geoJson(json_Administative_0, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Administative_0',
            layerName: 'layer_Administative_0',
            pane: 'pane_Administative_0',
            onEachFeature: pop_Administative_0,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.circleMarker(latlng, style_Administative_0_0(feature));
            },
        });
        bounds_group.addLayer(layer_Administative_0);
        map.addLayer(layer_Administative_0);
        function pop_Boundary_1(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['id'] !== null ? autolinker.link(feature.properties['id'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Boundary_1_0() {
            return {
                pane: 'pane_Boundary_1',
                opacity: 1,
                color: 'rgba(224,27,28,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 1.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_Boundary_1');
        map.getPane('pane_Boundary_1').style.zIndex = 401;
        map.getPane('pane_Boundary_1').style['mix-blend-mode'] = 'normal';
        var layer_Boundary_1 = new L.geoJson(json_Boundary_1, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Boundary_1',
            layerName: 'layer_Boundary_1',
            pane: 'pane_Boundary_1',
            onEachFeature: pop_Boundary_1,
            style: style_Boundary_1_0,
        });
        bounds_group.addLayer(layer_Boundary_1);
        map.addLayer(layer_Boundary_1);
        function pop_Banks_2(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Bank_names'] !== null ? autolinker.link(feature.properties['Bank_names'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Banks_2_0() {
            return {
                pane: 'pane_Banks_2',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/money_bank2.svg',
            iconSize: [11.399999999999999, 11.399999999999999]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_Banks_2');
        map.getPane('pane_Banks_2').style.zIndex = 402;
        map.getPane('pane_Banks_2').style['mix-blend-mode'] = 'normal';
        var layer_Banks_2 = new L.geoJson(json_Banks_2, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Banks_2',
            layerName: 'layer_Banks_2',
            pane: 'pane_Banks_2',
            onEachFeature: pop_Banks_2,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_Banks_2_0(feature));
            },
        });
        bounds_group.addLayer(layer_Banks_2);
        map.addLayer(layer_Banks_2);
        function pop_FillingStation_3(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Filling_station'] !== null ? autolinker.link(feature.properties['Filling_station'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_FillingStation_3_0() {
            return {
                pane: 'pane_FillingStation_3',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/transport_fuel.svg',
            iconSize: [15.2, 15.2]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_FillingStation_3');
        map.getPane('pane_FillingStation_3').style.zIndex = 403;
        map.getPane('pane_FillingStation_3').style['mix-blend-mode'] = 'normal';
        var layer_FillingStation_3 = new L.geoJson(json_FillingStation_3, {
            attribution: '',
            interactive: true,
            dataVar: 'json_FillingStation_3',
            layerName: 'layer_FillingStation_3',
            pane: 'pane_FillingStation_3',
            onEachFeature: pop_FillingStation_3,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_FillingStation_3_0(feature));
            },
        });
        bounds_group.addLayer(layer_FillingStation_3);
        map.addLayer(layer_FillingStation_3);
        function pop_Healthfacilities_4(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Hospital'] !== null ? autolinker.link(feature.properties['Hospital'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Healthfacilities_4_0() {
            return {
                pane: 'pane_Healthfacilities_4',
                radius: 6.0,
                opacity: 1,
                color: 'rgba(35,35,35,1.0)',
                dashArray: '',
                lineCap: 'butt',
                lineJoin: 'miter',
                weight: 1,
                fill: true,
                fillOpacity: 1,
                fillColor: 'rgba(231,22,29,1.0)',
                interactive: true,
            }
        }
        map.createPane('pane_Healthfacilities_4');
        map.getPane('pane_Healthfacilities_4').style.zIndex = 404;
        map.getPane('pane_Healthfacilities_4').style['mix-blend-mode'] = 'normal';
        var layer_Healthfacilities_4 = new L.geoJson(json_Healthfacilities_4, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Healthfacilities_4',
            layerName: 'layer_Healthfacilities_4',
            pane: 'pane_Healthfacilities_4',
            onEachFeature: pop_Healthfacilities_4,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.shapeMarker(latlng, style_Healthfacilities_4_0(feature));
            },
        });
        bounds_group.addLayer(layer_Healthfacilities_4);
        map.addLayer(layer_Healthfacilities_4);
        function pop_Hotels_5(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Hotels'] !== null ? autolinker.link(feature.properties['Hotels'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Hotels_5_0() {
            return {
                pane: 'pane_Hotels_5',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/accommodation_hotel2.svg',
            iconSize: [15.2, 15.2]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_Hotels_5');
        map.getPane('pane_Hotels_5').style.zIndex = 405;
        map.getPane('pane_Hotels_5').style['mix-blend-mode'] = 'normal';
        var layer_Hotels_5 = new L.geoJson(json_Hotels_5, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Hotels_5',
            layerName: 'layer_Hotels_5',
            pane: 'pane_Hotels_5',
            onEachFeature: pop_Hotels_5,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_Hotels_5_0(feature));
            },
        });
        bounds_group.addLayer(layer_Hotels_5);
        map.addLayer(layer_Hotels_5);
        function pop_Others_6(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['others_prominent_features'] !== null ? autolinker.link(feature.properties['others_prominent_features'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Others_6_0() {
            return {
                pane: 'pane_Others_6',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/background_triangle.svg',
            iconSize: [11.399999999999999, 11.399999999999999]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_Others_6');
        map.getPane('pane_Others_6').style.zIndex = 406;
        map.getPane('pane_Others_6').style['mix-blend-mode'] = 'normal';
        var layer_Others_6 = new L.geoJson(json_Others_6, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Others_6',
            layerName: 'layer_Others_6',
            pane: 'pane_Others_6',
            onEachFeature: pop_Others_6,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_Others_6_0(feature));
            },
        });
        bounds_group.addLayer(layer_Others_6);
        map.addLayer(layer_Others_6);
        function pop_Recreational_centres_7(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Recreational_centres'] !== null ? autolinker.link(feature.properties['Recreational_centres'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Recreational_centres_7_0() {
            return {
                pane: 'pane_Recreational_centres_7',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/background_security_02.svg',
            iconSize: [11.399999999999999, 11.399999999999999]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_Recreational_centres_7');
        map.getPane('pane_Recreational_centres_7').style.zIndex = 407;
        map.getPane('pane_Recreational_centres_7').style['mix-blend-mode'] = 'normal';
        var layer_Recreational_centres_7 = new L.geoJson(json_Recreational_centres_7, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Recreational_centres_7',
            layerName: 'layer_Recreational_centres_7',
            pane: 'pane_Recreational_centres_7',
            onEachFeature: pop_Recreational_centres_7,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_Recreational_centres_7_0(feature));
            },
        });
        bounds_group.addLayer(layer_Recreational_centres_7);
        map.addLayer(layer_Recreational_centres_7);
        function pop_Restaurant_8(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['restraurants'] !== null ? autolinker.link(feature.properties['restraurants'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Restaurant_8_0() {
            return {
                pane: 'pane_Restaurant_8',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/food_restaurant.svg',
            iconSize: [15.2, 15.2]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_Restaurant_8');
        map.getPane('pane_Restaurant_8').style.zIndex = 408;
        map.getPane('pane_Restaurant_8').style['mix-blend-mode'] = 'normal';
        var layer_Restaurant_8 = new L.geoJson(json_Restaurant_8, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Restaurant_8',
            layerName: 'layer_Restaurant_8',
            pane: 'pane_Restaurant_8',
            onEachFeature: pop_Restaurant_8,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_Restaurant_8_0(feature));
            },
        });
        bounds_group.addLayer(layer_Restaurant_8);
        map.addLayer(layer_Restaurant_8);
        function pop_Schools_9(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['schools'] !== null ? autolinker.link(feature.properties['schools'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Schools_9_0() {
            return {
                pane: 'pane_Schools_9',
        rotationAngle: 0.0,
        rotationOrigin: 'center center',
        icon: L.icon({
            iconUrl: 'markers/education_university.svg',
            iconSize: [15.2, 15.2]
        }),
                interactive: true,
            }
        }
        map.createPane('pane_Schools_9');
        map.getPane('pane_Schools_9').style.zIndex = 409;
        map.getPane('pane_Schools_9').style['mix-blend-mode'] = 'normal';
        var layer_Schools_9 = new L.geoJson(json_Schools_9, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Schools_9',
            layerName: 'layer_Schools_9',
            pane: 'pane_Schools_9',
            onEachFeature: pop_Schools_9,
            pointToLayer: function (feature, latlng) {
                var context = {
                    feature: feature,
                    variables: {}
                };
                return L.marker(latlng, style_Schools_9_0(feature));
            },
        });
        bounds_group.addLayer(layer_Schools_9);
        map.addLayer(layer_Schools_9);
        function pop_Roundabouts_10(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['SHAPE_Length'] !== null ? autolinker.link(feature.properties['SHAPE_Length'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['SHAPE_Area'] !== null ? autolinker.link(feature.properties['SHAPE_Area'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Roundabouts_10_0() {
            return {
                pane: 'pane_Roundabouts_10',
                opacity: 1,
                color: 'rgba(134,0,42,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 4.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_Roundabouts_10');
        map.getPane('pane_Roundabouts_10').style.zIndex = 410;
        map.getPane('pane_Roundabouts_10').style['mix-blend-mode'] = 'normal';
        var layer_Roundabouts_10 = new L.geoJson(json_Roundabouts_10, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Roundabouts_10',
            layerName: 'layer_Roundabouts_10',
            pane: 'pane_Roundabouts_10',
            onEachFeature: pop_Roundabouts_10,
            style: style_Roundabouts_10_0,
        });
        bounds_group.addLayer(layer_Roundabouts_10);
        map.addLayer(layer_Roundabouts_10);
        function pop_Majorroads_11(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['Major_Road_names'] !== null ? autolinker.link(feature.properties['Major_Road_names'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['SHAPE_Length'] !== null ? autolinker.link(feature.properties['SHAPE_Length'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Majorroads_11_0() {
            return {
                pane: 'pane_Majorroads_11',
                opacity: 1,
                color: 'rgba(187,0,31,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 4.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_Majorroads_11');
        map.getPane('pane_Majorroads_11').style.zIndex = 411;
        map.getPane('pane_Majorroads_11').style['mix-blend-mode'] = 'normal';
        var layer_Majorroads_11 = new L.geoJson(json_Majorroads_11, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Majorroads_11',
            layerName: 'layer_Majorroads_11',
            pane: 'pane_Majorroads_11',
            onEachFeature: pop_Majorroads_11,
            style: style_Majorroads_11_0,
        });
        bounds_group.addLayer(layer_Majorroads_11);
        map.addLayer(layer_Majorroads_11);
        function pop_Railway_12(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['SHAPE_Length'] !== null ? autolinker.link(feature.properties['SHAPE_Length'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Railway_12_0() {
            return {
                pane: 'pane_Railway_12',
                opacity: 1,
                color: 'rgba(0,0,0,1.0)',
                dashArray: '',
                lineCap: 'round',
                lineJoin: 'round',
                weight: 1.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        function style_Railway_12_1() {
            return {
                pane: 'pane_Railway_12',
                interactive: true,
            }
        }
        map.createPane('pane_Railway_12');
        map.getPane('pane_Railway_12').style.zIndex = 412;
        map.getPane('pane_Railway_12').style['mix-blend-mode'] = 'normal';
        var layer_Railway_12 = new L.geoJson.multiStyle(json_Railway_12, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Railway_12',
            layerName: 'layer_Railway_12',
            pane: 'pane_Railway_12',
            onEachFeature: pop_Railway_12,
            styles: [style_Railway_12_0,style_Railway_12_1,]
        });
        bounds_group.addLayer(layer_Railway_12);
        map.addLayer(layer_Railway_12);
        function pop_Streets_13(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['street_names'] !== null ? autolinker.link(feature.properties['street_names'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['SHAPE_Length'] !== null ? autolinker.link(feature.properties['SHAPE_Length'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Streets_13_0() {
            return {
                pane: 'pane_Streets_13',
                opacity: 1,
                color: 'rgba(195,196,191,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 2.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_Streets_13');
        map.getPane('pane_Streets_13').style.zIndex = 413;
        map.getPane('pane_Streets_13').style['mix-blend-mode'] = 'normal';
        var layer_Streets_13 = new L.geoJson(json_Streets_13, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Streets_13',
            layerName: 'layer_Streets_13',
            pane: 'pane_Streets_13',
            onEachFeature: pop_Streets_13,
            style: style_Streets_13_0,
        });
        bounds_group.addLayer(layer_Streets_13);
        map.addLayer(layer_Streets_13);
        function pop_Minorroads_14(feature, layer) {
            layer.on({
                mouseout: function(e) {
                    for (i in e.target._eventParents) {
                        e.target._eventParents[i].resetStyle(e.target);
                    }
                },
                mouseover: highlightFeature,
            });
            var popupContent = '<table>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['OBJECTID'] !== null ? autolinker.link(feature.properties['OBJECTID'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['monor_road_name'] !== null ? autolinker.link(feature.properties['monor_road_name'].toLocaleString()) : '') + '</td>\
                    </tr>\
                    <tr>\
                        <td colspan="2">' + (feature.properties['SHAPE_Length'] !== null ? autolinker.link(feature.properties['SHAPE_Length'].toLocaleString()) : '') + '</td>\
                    </tr>\
                </table>';
            layer.bindPopup(popupContent, {maxHeight: 400});
        }

        function style_Minorroads_14_0() {
            return {
                pane: 'pane_Minorroads_14',
                opacity: 1,
                color: 'rgba(19,20,19,1.0)',
                dashArray: '',
                lineCap: 'square',
                lineJoin: 'bevel',
                weight: 3.0,
                fillOpacity: 0,
                interactive: true,
            }
        }
        map.createPane('pane_Minorroads_14');
        map.getPane('pane_Minorroads_14').style.zIndex = 414;
        map.getPane('pane_Minorroads_14').style['mix-blend-mode'] = 'normal';
        var layer_Minorroads_14 = new L.geoJson(json_Minorroads_14, {
            attribution: '',
            interactive: true,
            dataVar: 'json_Minorroads_14',
            layerName: 'layer_Minorroads_14',
            pane: 'pane_Minorroads_14',
            onEachFeature: pop_Minorroads_14,
            style: style_Minorroads_14_0,
        });
        bounds_group.addLayer(layer_Minorroads_14);
        map.addLayer(layer_Minorroads_14);
        var osmGeocoder = new L.Control.Geocoder({
            collapsed: true,
            position: 'topleft',
            text: 'Search',
            title: 'Testing'
        }).addTo(map);
        document.getElementsByClassName('leaflet-control-geocoder-icon')[0]
        .className += ' fa fa-search';
        document.getElementsByClassName('leaflet-control-geocoder-icon')[0]
        .title += 'Search for a place';
        var baseMaps = {};
        L.control.layers(baseMaps,{'<img src="legend/Minorroads_14.png" /> Minorroads': layer_Minorroads_14,'<img src="legend/Streets_13.png" /> Streets': layer_Streets_13,'<img src="legend/Railway_12.png" /> Railway': layer_Railway_12,'<img src="legend/Majorroads_11.png" /> Majorroads': layer_Majorroads_11,'<img src="legend/Roundabouts_10.png" /> Roundabouts': layer_Roundabouts_10,'<img src="legend/Schools_9.png" /> Schools': layer_Schools_9,'<img src="legend/Restaurant_8.png" /> Restaurant': layer_Restaurant_8,'<img src="legend/Recreational_centres_7.png" /> Recreational_centres': layer_Recreational_centres_7,'<img src="legend/Others_6.png" /> Others': layer_Others_6,'<img src="legend/Hotels_5.png" /> Hotels': layer_Hotels_5,'<img src="legend/Healthfacilities_4.png" /> Health facilities': layer_Healthfacilities_4,'<img src="legend/FillingStation_3.png" /> FillingStation': layer_FillingStation_3,'<img src="legend/Banks_2.png" /> Banks': layer_Banks_2,'<img src="legend/Boundary_1.png" /> Boundary ': layer_Boundary_1,'<img src="legend/Administative_0.png" /> Administative': layer_Administative_0,}).addTo(map);
        setBounds();
        var i = 0;
        layer_Administative_0.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Administative_Blds'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Administative_Blds']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Administative_0'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Banks_2.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Bank_names'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Bank_names']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Banks_2'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_FillingStation_3.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Filling_station'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Filling_station']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_FillingStation_3'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Healthfacilities_4.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Hospital'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Hospital']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Healthfacilities_4'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Hotels_5.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Hotels'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Hotels']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Hotels_5'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Others_6.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['others_prominent_features'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['others_prominent_features']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Others_6'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Recreational_centres_7.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Recreational_centres'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Recreational_centres']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Recreational_centres_7'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Restaurant_8.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['restraurants'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['restraurants']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Restaurant_8'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Schools_9.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['schools'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['schools']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Schools_9'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Majorroads_11.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['Major_Road_names'] !== null?String('<div style="color: #000000; font-size: 10pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['Major_Road_names']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Majorroads_11'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Streets_13.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['street_names'] !== null?String('<div style="color: #000000; font-size: 7pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['street_names']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Streets_13'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        var i = 0;
        layer_Minorroads_14.eachLayer(function(layer) {
            var context = {
                feature: layer.feature,
                variables: {}
            };
            layer.bindTooltip((layer.feature.properties['monor_road_name'] !== null?String('<div style="color: #000000; font-size: 8pt; font-family: \'MS Shell Dlg 2\', sans-serif;">' + layer.feature.properties['monor_road_name']) + '</div>':''), {permanent: true, offset: [-0, -16], className: 'css_Minorroads_14'});
            labels.push(layer);
            totalMarkers += 1;
              layer.added = true;
              addLabel(layer, i);
              i++;
        });
        map.addControl(new L.Control.Search({
            layer: layer_Minorroads_14,
            initial: false,
            hideMarkerOnCollapse: true,
            propertyName: 'monor_road_name'}));
        document.getElementsByClassName('search-button')[0].className +=
         ' fa fa-binoculars';
        resetLabels([layer_Administative_0,layer_Banks_2,layer_FillingStation_3,layer_Healthfacilities_4,layer_Hotels_5,layer_Others_6,layer_Recreational_centres_7,layer_Restaurant_8,layer_Schools_9,layer_Majorroads_11,layer_Streets_13,layer_Minorroads_14]);
        map.on("zoomend", function(){
            resetLabels([layer_Administative_0,layer_Banks_2,layer_FillingStation_3,layer_Healthfacilities_4,layer_Hotels_5,layer_Others_6,layer_Recreational_centres_7,layer_Restaurant_8,layer_Schools_9,layer_Majorroads_11,layer_Streets_13,layer_Minorroads_14]);
        });
        map.on("layeradd", function(){
            resetLabels([layer_Administative_0,layer_Banks_2,layer_FillingStation_3,layer_Healthfacilities_4,layer_Hotels_5,layer_Others_6,layer_Recreational_centres_7,layer_Restaurant_8,layer_Schools_9,layer_Majorroads_11,layer_Streets_13,layer_Minorroads_14]);
        });
        map.on("layerremove", function(){
            resetLabels([layer_Administative_0,layer_Banks_2,layer_FillingStation_3,layer_Healthfacilities_4,layer_Hotels_5,layer_Others_6,layer_Recreational_centres_7,layer_Restaurant_8,layer_Schools_9,layer_Majorroads_11,layer_Streets_13,layer_Minorroads_14]);
        });
        </script>
    </body>
</html>
