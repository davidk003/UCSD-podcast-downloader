<script lang="ts">
	import Button from '$lib/components/ui/button/button.svelte';
    import { SvelteMap } from 'svelte/reactivity';
	import NumberFlow, { continuous } from '@number-flow/svelte';
	

    let counters = new SvelteMap<string, number>([
        ["Videos scraped", 0],
        ["Videos served", 0],
        ["Average response time", 0],
        ["Unique Classes", 0]
    ]);
	$: value = Math.floor(Math.random() * Math.random() * 10000000);

    setInterval(() => {
        updateCounts();
    }, 1000);

    function updateCounts() {

        for (const [key, value] of counters) {
            counters.set(key, Math.floor(Math.random() * Math.random() * 10000000));
        }

    }
</script>

<h1 class="m-5 text-center text-3xl font-semibold">Analytics</h1>

<div class="flex flex-col items-center justify-center gap-4 md:flex-row">

{#each counters as [key, value]}
<div class="flex flex-col items-center">
    <h3 class="m-5 text-center text-2xl font-semibold">{key}</h3>
    <NumberFlow
        class="gap-4 font-semibold text-4xl"
        {value}
        locales="en-US"
        trend={+1}
        plugins={[continuous]}
        transformTiming={{ duration: 750, easing: 'linear(...)' }}
        spinTiming={{ duration: 750, easing: 'linear(...)' }}
        opacityTiming={{ duration: 350, easing: 'ease-out' }}
    />
</div>
{/each}
</div>