<script lang="ts">

    type soundMeta = {
        title: string
        loc: Array<number>
        desc: string
        time: string
    }
	let { items, OnSelect }: { items: soundMeta[], OnSelect: (idx: number) => void } = $props();


</script>
<ul class="bg-white font-sans">
    {#each items as item, idx}
        <li class="tracking-wide [paint-order:stroke_fill] [-webkit-text-stroke:6px_white]" id="{idx.toString()}">

            <button class="w-full max-w-full p-2" onclick={() => OnSelect(idx)}>

                <div class="flex flex-row mb-2">

                    <div class="flex flex-row items-start gap-2 w-1/2 min-w-0">
                        <img src="/Cassete.png" alt="" class="shrink-0 mt-[0.3rem] [image-rendering:pixelated] size-5">
                        <div class="felx flex-col">
                            <p class="min-w-0 font-medium text-xl truncate">{item.title}</p>
                            <p class="text-xs text-start italic">{item.loc[1]}, {item.loc[0]}</p>
                        </div>
                    </div>

                    <div class="grow flex items-start justify-end pt-1">
                        <p class="text-sm italic">{item.time}</p>
                    </div>
                </div>
                <p class="text-start">{item.desc}</p>
            </button>
        </li>
    {/each}
</ul>
