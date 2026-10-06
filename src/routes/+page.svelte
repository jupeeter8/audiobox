<script lang="ts">
    import { onMount } from 'svelte';
    import  SoundCard  from '$lib/components/SoundCard.svelte';
    import Title from '$lib/components/Title.svelte';
    import data from '$lib/data/metadata.json'

    import {Map, setWorkerUrl, Marker} from 'maplibre-gl';
    import 'maplibre-gl/dist/maplibre-gl.css';
    import workerUrl from 'maplibre-gl/dist/maplibre-gl-worker.mjs?worker&url';

    setWorkerUrl(workerUrl);



    onMount(() =>{
        const map = new Map({
            container: 'map',
            style: {
                "version": 8,
                "name": "watercolor",
                "sources": {
                    "stadia": {
                        "type": "raster",
                        "tiles": [
                            "https://tiles.stadiamaps.com/tiles/stamen_watercolor/{z}/{x}/{y}.jpg"
                        ],
                        "tileSize": 256
                    },
                    "labels": {
                      "type": "raster",
                      "tiles": ["https://tiles.stadiamaps.com/tiles/stamen_terrain_labels/{z}/{x}/{y}@2x.png"],
                      "tileSize": 256,
                    },
                },
                "layers": [
                    {"id": "testlayer", "source": "stadia", "type": "raster"},
                    { id: "labels", type: "raster", source: "labels" }
                ]
            },
            center: [126.975901, 37.578605],
            zoom: 14
        });


        new Marker().setLngLat([126.975901, 37.578605]).addTo(map);

    })

    function setMapView(lat: number, long: number) {
        return
    }

    let audioPlayer: any;
    let path = $state(`/records/${data[0].fileName}`)
    function OnSelect(idx: number) {
        path = `/records/${data[idx].fileName}`
        audioPlayer.load()
        map 
    }
</script>
<div class="w-4/5 m-auto h-[50vh] max-h-[50vh] flex flex-col mt-20 mb-3">

    <Title></Title>

    <div class="max-h-full">
        <nav class="flex flex-col overflow-scroll max-h-[75%]">
            <SoundCard items={data} {OnSelect}>
            </SoundCard>
        </nav>
    </div>
</div>
<div id=map class="h-50 w-[100vw]">
</div>
<div>
    <audio bind:this={audioPlayer} src="{path}" controls></audio>
</div>
