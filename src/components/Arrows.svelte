<script>
    import Arrow from "./Arrow.svelte"

    import { getContext, createEventDispatcher } from "svelte"

    const { data, xGet, yGet } = getContext('LayerCake')

    const dispatch = createEventDispatcher()
</script>

<defs>
    <marker id="arrow-neg" viewBox="0 -5 10 10" refX="5" refY="0" markerWidth="2.5" markerHeight="2.5" orient="auto">
        <path d="M0,-5L10,0L0,5" class="arrowhead neg" fill="#ff9b5a"></path>
    </marker>
    <marker id="arrow-pos" viewBox="0 -5 10 10" refX="5" refY="0" markerWidth="2.5" markerHeight="2.5" orient="auto">
        <path d="M0,-5L10,0L0,5" class="arrowhead pos" fill="#9686f7"></path>
    </marker>
</defs>

<g class = "encoding"
    on:mouseout={(e) => dispatch('mouseout-arrows')}    
>
    {#each $data as d,i (i)}
        <Arrow
            x1 = {$xGet(d)[0]}
            x2 = {$xGet(d)[1]}
            translatedY = {$yGet(d)}
            class_sign = {d.Salary_2010 > d.Salary_2016}
            Abbr = {d.Abbr}
            {i}
            on:mouseover = {(e) => {
                dispatch('mousemove-rect', {e, props: d})
            }}
        >
        {d.Abbr}
        </Arrow>   
    {/each}
</g>