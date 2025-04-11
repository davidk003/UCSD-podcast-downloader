<script lang="ts">
    import { SvelteMap } from 'svelte/reactivity';
	import NumberFlow, { continuous } from '@number-flow/svelte';
	
    // Departments by scrape count
    // By year
    // By professor
    // Requests by location

    let counters = new SvelteMap<string, number>([
        ["Video downloads", 0],
        ["Videos served", 0],
        ["Unique classes", 0],
        ["Video time scraped", 0],
        ["Uptime", 0],
        ["Scrape failure rate", 0],
        ["Average response time", 0],
        ["Requests per day", 0],
    ]);
	// $: value = Math.floor(Math.random() * Math.random() * 10000000);
    for(const [key, value] of counters) {
        counters.set(key, Math.floor(Math.random() * Math.random() * 10000000))
    }

    setInterval(() => {
        updateCounts();
    }, 750);

    function updateCounts() {

        for (const [key, value] of counters) {
            if(Math.floor(Math.random()*3) == 1) {
                counters.set(key, value+1);
            }
        }

    }
</script>

<h1 class="m-5 text-center text-4xl font-semibold">Analytics</h1>

{#each counters as [key, value]}

        <div class="flex flex-row gap-4 items-center justify-center m-5 text-2xl">
            <h3 class="font-semibold">{key}</h3>
        <NumberFlow
                style="--number-flow-char-height: 0.85em; overflow: hidden;"
                class="font-semibold font-variant-numeric: tabular-nums"
            value={value}
            locales="en-US"
            trend={+1}
            respectMotionPreference={false}
            plugins={[continuous]}
            willChange={true}
            />
    </div>

{/each}