<script>
    import { SankeyChartComponent } from "@visuallyjs/browser-ui-svelte";

    let { url = "/dataset.json" } = $props();
    let pivot = $state('transitMode');

</script>

<div style="position: relative;">
    <div class="controls-panel">
        <label class="pivot-label" for="pivot-select">Pivot:</label>
        <select 
            id="pivot-select"
            class="pivot-select"
            bind:value={pivot}
        >
            <option value="">No pivot</option>
            <option value="transitMode">Transit Mode</option>
            <option value="carrier">Carrier</option>
        </select>
    </div>
    <SankeyChartComponent
        {url}
        {pivot}
        options={{
            linkColorStrategy: "source-target",
            labelProperty:"name",
            labels: {
                padding: 5,
                backgroundColor: "#FFFFFF56"
            },
            tooltipSuffix: "TWh"
        }}
    />
</div>
