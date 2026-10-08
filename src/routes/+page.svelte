<script lang="ts">
    import  SoundCard  from '$lib/components/SoundCard.svelte';
    import Title from '$lib/components/Title.svelte';
    import data from '$lib/data/metadata.json';
    import Map from '$lib/components/Map.svelte';

    function setMapView(lat: number, long: number) {
        return
    }

    let currentLoc = 0
    let audioPlayer: any;
    let path = $state(`/records/${data[0].fileName}`)
    let marker = $state(data[0].loc)
    let inMapAnimation = $state(false)

    function OnSelect(idx: number) {
        if (currentLoc != idx) {
            currentLoc = idx
            path = `/records/${data[idx].fileName}`
            marker =  data[idx].loc
            inMapAnimation = true
            //audioPlayer.load()
        }
    }


</script>
<div class="fixed z-999  flex flex-col justify-between items-center min-h-full pointer-events-none sm:w-full sm:max-w-full">
    <Title inMapAnimation={inMapAnimation}></Title>
        <nav class="flex flex-col overflow-scroll m-2 max-h-[20vh] px-2 pointer-events-auto transition-opacity duration-700 ease-in-out {inMapAnimation ? 'opacity-0' : 'opacity-100'}">
            <SoundCard items={data} {OnSelect}>
            </SoundCard>
        </nav>
</div>
<Map marker={marker} bind:inMapAnimation={inMapAnimation}></Map>

<!--<div class="relative z-999">
    <audio class="fixed bottom-4 left-1/2 -translate-x-1/2 z-50" bind:this={audioPlayer} src="{path}" controls></audio>
</div>-->
