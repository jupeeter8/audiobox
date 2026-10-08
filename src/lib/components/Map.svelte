<script lang="ts">
    import { onMount } from 'svelte';
    import {Map, setWorkerUrl, Marker} from 'maplibre-gl';
    import 'maplibre-gl/dist/maplibre-gl.css';
    import workerUrl from 'maplibre-gl/dist/maplibre-gl-worker.mjs?worker&url';
    setWorkerUrl(workerUrl);

    let { marker, inMapAnimation = $bindable() }: { marker: number[], inMapAnimation: boolean }= $props()

    let map
    let mapMarker
    let mapContainer = 'map'

    onMount(() =>{
        map = new Map({
            container: mapContainer,
            style: {
                "version": 8,
                "name": "watercolor",
                "sources": {
                    "stadia": {
                        "type": "raster",
                        "tiles": [
                            "https://tiles.stadiamaps.com/tiles/stamen_watercolor/{z}/{x}/{y}.jpg"
                        ],
                        "tileSize": 512
                    },
                    "labels": {
                        "type": "raster",
                        "tiles": ["https://tiles.stadiamaps.com/tiles/stamen_terrain_labels/{z}/{x}/{y}@2x.png"],
                        "tileSize": 512,
                    },
                    "osm": {
                      "type": "raster",
                      "tiles": ["https://tile.openstreetmap.org/{z}/{x}/{y}.png"],
                      "tileSize": 256,
                    }
                },
                "layers": [
                    {"id": "watercolour", "source": "stadia", "type": "raster"},
                    {"id": "osm", "source": "osm", "type": "raster", paint: { "raster-opacity": 0.4 }},
                    { id: "labels", type: "raster", source: "labels" }
                ]
            },
            zoom: 14
        });

        map.setCenter(marker)
        mapMarker = new Marker().setLngLat(marker).addTo(map);
    })

    $effect(() => {
        map.flyTo({center: marker, zoom: 14, speed: 2.2})
        map.once('moveend', (e) => {
            mapMarker.setLngLat(marker).addTo(map)
            inMapAnimation = false
        });
    })

</script>
<div bind:this={mapContainer} id=map class="h-[100vh] w-[100vw]"></div>
