<script lang="ts">
    let { inMapAnimation }: { inMapAnimation: boolean } = $props()


</script>
<div id="pageTitle" class="transition-opacity duration-700 ease-in-out {inMapAnimation ? 'opacity-0' : 'opacity-100'} pointer-events-none top-0 left-0 flex w-full justify-center">
    <div
        class="flex w-[70vw] max-w-4xl justify-center py-16"
    >
        <h1 class="font-title pointer-events-auto text-5xl  text-gray-800 [paint-order:stroke_fill] [-webkit-text-stroke:16px_white] [text-stroke:16px_white] [text-shadow:0_0_5px_white,0_0_5px_white]">Soundgarden</h1>
    </div>
</div>
