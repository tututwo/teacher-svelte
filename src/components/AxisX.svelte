<script>
    import { getContext } from "svelte"
    import { format } from "d3-format"

    const { width, height, xScale, yRange } = getContext("LayerCake")

    const num_format = format(".2s")
    $: tickVal = $xScale.ticks(5)
    $: formatted_val = tickVal.map(d => num_format(d))

    $: console.log($height)
</script>

<g class = "x-axis">
    {#each tickVal as d,i}
        <g class = "tick"
        >
            <line stroke="#000" x1 = {$xScale(d)} y1 = 0 x2 = {$xScale(d)} y2 = {$yRange[1]-10}></line>
            <text transform = "translate({$xScale(d)-10},{$yRange[0]-10})">${num_format(d)}</text>
            <text transform = "translate({$xScale(d)-10},{$yRange[1]})">${num_format(d)}</text>
        </g>
    {/each}
</g>

<style>
    line {
        stroke: #aaa;
        stroke-dasharray: 2;
        pointer-events: none;
    }

    text {
        font-family: "Liberation Mono",monospace;
        fill: #858585;
        pointer-events: none;
        font-size: 0.8em;
    }
</style>
