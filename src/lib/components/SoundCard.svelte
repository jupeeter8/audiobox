<script lang="ts">

    type soundMeta = {
        title: string
        loc: Array<number>
        desc: string
        time: string
    }
	let { items, OnSelect }: { items: soundMeta[], OnSelect: (idx: number) => void } = $props();


</script>
<ul class="font-sans tracking-wide [paint-order:stroke_fill] [-webkit-text-stroke:6px_white]">
    {#each items as item, idx}
        <li class="bg-white m-2 rounded-md" id="{idx.toString()}">

            <button class="w-full max-w-full p-2" onclick={() => OnSelect(idx)}>

                <div class="flex flex-row items-start gap-2 w-full">
                    <img src="/Cassete.png" alt="" class="shrink-0 mt-[0.3rem] [image-rendering:pixelated] size-5">
                    <div class="flex flex-col grow min-w-0 text-start">
                        <div class="flex flex-row mb-0.5">
                            <div class="flex flex-col w-1/2 min-w-0">
                                <p class="font-medium text-xl truncate">{item.title}</p>
                                <p class="text-xs text-gray-500 italic">{item.loc[1]}, {item.loc[0]}</p>
                            </div>
                            <div class="flex grow justify-end pt-0.5">
                                <p class="text-sm italic text-gray-500">{item.time}</p>
                            </div>
                        </div>
                        <p class="truncate">{item.desc}</p>
                    </div>
                </div>
            </button>
        </li>
    {/each}
</ul>
