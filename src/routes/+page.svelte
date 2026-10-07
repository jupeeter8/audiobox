<script lang="ts">
    import { onMount } from 'svelte';
    import  SoundCard  from '$lib/components/SoundCard.svelte';
    import Title from '$lib/components/Title.svelte';
    import data from '$lib/data/metadata.json';
    import Map from '$lib/components/Map.svelte';

    function setMapView(lat: number, long: number) {
        return
    }

    let audioPlayer: any;
    let path = $state(`/records/${data[0].fileName}`)
    let marker = $state(data[0].loc)

    function OnSelect(idx: number) {
        path = `/records/${data[idx].fileName}`
        marker =  data[idx].loc
        audioPlayer.load()
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
<Map marker={marker}></Map>
<div>
    <audio bind:this={audioPlayer} src="{path}" controls></audio>
</div>
