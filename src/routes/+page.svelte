<script lang="ts">
    import { onMount } from 'svelte';
    import  SoundCard  from '$lib/components/SoundCard.svelte';
    import Title from '$lib/components/Title.svelte';
    onMount(() =>{
        const L = window.L
        const map = L.map('map').setView([51.505, -0.09], 13);
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);
    })

    const dummyData = [
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
        {
            "title": "Brids in the zoo",
            "time": "3pm",
            "latt": "30.120",
            "long": "12.57",
            "desc": "Some things I recorded while walking in bengaluru"
        },
    ]
</script>
<div class="w-4/5 m-auto h-[50vh] max-h-[50vh] flex flex-col mt-20">

    <Title></Title>

    <div class="flex flex-row flex-1 max-h-full">
        <nav class="flex flex-col shrink-0 w-md overflow-scroll">
            <SoundCard items={dummyData}>
            </SoundCard>
        </nav>
        <div id=map class="flex-1">
        </div>
    </div>

</div>