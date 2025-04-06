<script lang="ts">
    import Button from '$lib/components/ui/button/button.svelte';
import NumberFlow, { continuous } from '@number-flow/svelte';
    const numbers = [0, 100, 200, 300, 400, 500];
    let idx = 0;
    $: value = numbers[idx % numbers.length];

    function incrementIndex() {
        idx++;
    }
</script>

<h1 class="text-3xl font-semibold text-center m-5">Analytics</h1>
<div>
    <NumberFlow value={value} trend={0} format={{ notation: "compact" }} class=""/>
    <Button on:click={incrementIndex} class="m-5">
    </Button>
</div>