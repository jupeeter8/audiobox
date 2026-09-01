<script lang="ts">
    type soundMeta = {
        title: string
        long: string
        latt: string
        desc: string
        time: string
    }
	let { items }: { items: soundMeta[] } = $props();
</script>
<ul>
    {#each items as item}
    <li class="flex items-start gap-3 mb-2">
        <img src="/Cassete.png" alt="" class="shrink-0 mt-[0.2rem] [image-rendering:pixelated] size-5">
        <div class="font-jet">
            <p class="font-semibold">{item.title}</p>
                <div class="flex justify-between">
                    <p>{item.long} {item.latt}</p>
                    <p>{item.time}</p>
                </div>
            <p>
                {item.desc}
            </p>
        </div>
    </li>
    {/each}
</ul>