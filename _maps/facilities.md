---
title: "SCHH Amenities"
description: "Interactive map showing all community facilities and amenities."
date: 2025-09-21
permalink: /maps/facilities
layout: map-post
---

# Facilities

{% include embed.html %}

<style>

  #main-wrapper {
      padding: 0;
  }
  #main-wrapper > .container > div:first-of-type > main {
      padding-right: 0;
      padding-left: 0;
  }
  #main-wrapper > .container > div:first-of-type > main > article > header {
      padding-right: calc(var(--bs-gutter-x) * .5);
      padding-left: calc(var(--bs-gutter-x) * .5);
  }
  #tail-wrapper {
      display: none;
  }
  #map {
      width: 100%;
  }

  :root {
    --building-color: #FF9800;
    --house-color: #0288D1;
    --shop-color: #7B1FA2;
    --warehouse-color: #558B2F;
  }

  /*
  * Property styles in unhighlighted state.
  */
  .property {
    --accent: #263238;
    align-items: center;
    background-color: #FFFFFF;
    border-radius: 50%;
    color: #263238;
    display: flex;
    font-size: 14px;
    gap: 15px;
    justify-content: center;
    padding: 4px;
    position: relative;
    transition: all 0.3s ease-out;
    height: 30px;
    width: 30px;
    transform: translateY(-9px);
  }

  .property.highlight .icon {
    color: var(--accent);
    font-size: 2em;
  }

  .property:not(.highlight) {
    background-color: var(--accent);
  }

  .property:not(.highlight)::after {
    border-top: 9px solid var(--accent);
  }

  .property::after {
    border-left: 9px solid transparent;
    border-right: 9px solid transparent;
    border-top: 9px solid #FFFFFF;
    content: "";
    height: 0;
    left: 50%;
    position: absolute;
    top: 90%;
    transform: translate(-50%, 0);
    transition: all 0.3s ease-out;
    width: 0;
    z-index: 1;
  }

  .property .icon {
    align-items: center;
    display: flex;
    justify-content: center;
    color: #FFFFFF;
  }

  .property .icon svg {
    height: 20px;
    width: auto;
  }

  .property .details {
    display: none;
    flex-direction: column;
    flex: 1;
  }

  .property .address {
    color: #9E9E9E;
    font-size: 10px;
    margin-bottom: 10px;
    margin-top: 5px;
  }

  .property .features {
    align-items: flex-end;
    display: flex;
    flex-direction: row;
    gap: 10px;
  }

  .property .features > div {
    align-items: center;
    background: #F5F5F5;
    border-radius: 5px;
    border: 1px solid #ccc;
    display: flex;
    font-size: 10px;
    gap: 5px;
    padding: 5px;
  }

  /*
  * Property styles in highlighted state.
  */
  .property.highlight {
    background-color: #FFFFFF;
    border-radius: 8px;
    box-shadow: 10px 10px 5px rgba(0, 0, 0, 0.2);
    height: 80px;
    padding: 8px 15px;
    width: auto;
  }

  .property.highlight::after {
    border-top: 9px solid #FFFFFF;
  }

  .property.highlight .details {
    display: flex;
  }

  .property.highlight .icon svg {
    width: 50px;
    height: 50px;
  }

</style>

<gmp-map center="32.3044810,-80.9572716" zoom="13" id="map" map-id="amenities-map"></gmp-map>

<script type="module">
    import { getMap, loadGeoJSON, addMarkers } from '{{ '/assets/js/gmap.js' | relative_url }}';

    (async () => {
        try {
            const map = await getMap('map');
            await loadGeoJSON(map, 'https://www.schh-commons.org/knowledge-base/geojson/Sun_City,_Hilton_Head.geojson', {strokeWeight: 1, zIndex: 2, fillOpacity: 0});
            addMarkers(map, 'https://www.schh-commons.org/knowledge-base/geojson/Amenity_Locations.geojson');
        } catch (error) {
            console.error('Error initializing map:', error);
        }
    })();

</script>