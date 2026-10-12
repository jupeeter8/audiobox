<script lang="ts">
    import  SoundCard  from '$lib/components/SoundCard.svelte';
    import Title from '$lib/components/Title.svelte';
    import data from '$lib/data/metadata.json';
    import Map from '$lib/components/Map.svelte';

    let currentLoc = 0
    let audioPlayer: any;
    let path = $state(`/records/${data[0].fileName}`)
    let marker = $state(data[0].loc)
    let inMapAnimation = $state(false)
    let audioPlaying = false

    function OnSelect(idx: number) {
        if (currentLoc != idx) {
            currentLoc = idx
            path = `/records/${data[idx].fileName}`
            marker =  data[idx].loc
            inMapAnimation = true
            audioPlayer.load()
        }
    }

    function playAudio(): void {
        if (!audioPlaying) {
            audioPlayer.play()
        } else  {
            audioPlayer.pause()
        }
        audioPlaying = !audioPlaying
    }




</script>
<div class="fixed inset-x-0 top-0 z-50 flex min-h-full w-full flex-col items-center justify-between px-2 pointer-events-none">
    <Title inMapAnimation={inMapAnimation}></Title>
    <span class="pointer-events-auto material-symbols-outlined" onclick={() => playAudio()}>play_pause</span>
        <nav class="w-full max-w-md sm:max-w-2xl flex flex-col overflow-y-auto overflow-x-hidden my-2 max-h-[30vh] px-2 pointer-events-auto transition-opacity duration-700 ease-in-out {inMapAnimation ? 'opacity-0' : 'opacity-100'}">
            <SoundCard items={data} {OnSelect}>
            </SoundCard>
        </nav>
</div>
<Map marker={marker} bind:inMapAnimation={inMapAnimation}></Map>

<audio class="hidden" bind:this={audioPlayer} src="{path}"></audio>
<style>
    .material-symbols-outlined {
      font-variation-settings:
      'FILL' 0,
      'wght' 400,
      'GRAD' 0,
      'opsz' 24
    }
</style>
