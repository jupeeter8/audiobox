<script lang="ts">

    type soundMeta = {
        title: string
        loc: Array<number>
        desc: string
        time: string
    }
	let { items, OnSelect }: { items: soundMeta[], OnSelect: (idx: number) => void } = $props();


</script>
<ul class="">
    {#each items as item, idx}
    <li class="flex items-start gap-2 mb-5 font-sans font-bold tracking-wide [paint-order:stroke_fill] [-webkit-text-stroke:6px_white]." id="{idx.toString()}" onclick={() => OnSelect(idx)}>
        <img src="/Cassete.png" alt="" class="shrink-0 mt-[0.2rem] [image-rendering:pixelated] size-5">
        <div>
            <p class="font-semibold text-2xl">{item.title}</p>
	    <p class="mb-1.5 italic text-sm">{item.loc[0]} {item.loc[1]}</p>
            <p >{item.desc}</p>
        </div>
	<p class="text-sm">{item.time}</p>
    </li>
    {/each}
</ul>
