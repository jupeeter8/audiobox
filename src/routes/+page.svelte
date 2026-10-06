<script lang="ts">
    import { onMount } from 'svelte';
    import  SoundCard  from '$lib/components/SoundCard.svelte';
    import Title from '$lib/components/Title.svelte';
    import data from '$lib/data/metadata.json'

    onMount(() =>{
        const L = window.L
        const map = L.map('map').setView([51.505, -0.09], 13);
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);
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
<div id=map class="h-50 w-[100vh]">
</div>
<div>
    <audio bind:this={audioPlayer} src="{path}" controls></audio>
</div>
