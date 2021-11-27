<script>
    import { LayerCake, Svg, Html } from "layercake"
    import { ascending, scaleBand } from "d3"

    import Arrows from "./components/Arrows.svelte"
    import Buttons from "./components/Buttons.svelte"
    import Tooltip from "./components/Tooltip.svelte"
    import AxisX from "./components/AxisX.svelte"
    import Legend from "./components/Legend.svelte"

    import data from "./data/teachers.csv"
    import metrics from "./data/metrics";

    data.forEach(d => {
        d.Salary_2010 = +d.Salary_2010
        d.Salary_2016 = +d.Salary_2016
    });

    $: clicked_type = metrics[0].label
    $: filtered_data = data.filter(d => d.Type == clicked_type)
                        //    .sort((a,b) => ascending(a.Salary_2016, b.Salary_2016))
                        .sort((a, b) => ascending(a.Abbr, b.Abbr))
    // $: yScale = scaleBand().domain(data1.map(d => d.Abbr)).range([0,1000])
    
	$: xKey = ["Salary_2010", "Salary_2016"]
  
    // fixed y scaled to trigger animation
	let adjusted_cost_band = ["MI", "PA", "OH", "MA", "KY", "IA", "IL", "NJ", "GA", "WY", "MN", "DE", "NY", "WI", "IN", "CT", "MD", "RI", "OR", "NE", "AL", "NV", "CA", "TX", "AR", "TN", "DC", "MT", "AK", "KS", "MO", "NC", "ND", "ID", "VT", "SC", "MS", "OK", "LA", "VA", "FL", "WV", "NH", "CO", "NM", "UT", "WA", "AZ", "ME", "SD", "HI"]
	let actual_cost_band = ["NY", "MA", "DC", "CA", "CT", "NJ", "AK", "MD", "RI", "PA", "MI", "IL", "OR", "MN", "DE", "VT", "NH", "WY", "HI", "NV", "OH", "WI", "IA", "GA", "WA", "TX", "KY", "NE", "MT", "VA", "IN", "ND", "ME", "CO", "AL", "FL", "KS", "TN", "SC", "AR", "NC", "MO", "NM", "LA", "UT", "WV", "AZ", "ID", "OK", "MS", "SD"]
	
    // tooltip
    let hideTooltip = true;
    let evt
  
</script>

<!-- use bind, and event forwarding     on:click = {handleClick}-->
<Buttons 
    bind:clicked_type
/>

<figure>
    <LayerCake
        data = {filtered_data}
        x = {xKey}
        y = {"Abbr"}
        xDomain = {[40000, 80000]}
        yScale = {scaleBand()}
        yDomain = {clicked_type == 'Actual dollars' ? actual_cost_band : adjusted_cost_band}
        yReverse = true
    >

        <Svg>
            <AxisX />
            <Arrows 
                on:mousemove-rect = {event => evt = hideTooltip = event}
                on:mouseout-arrows = {(e) => hideTooltip = true}
            />

   
        </Svg>
        <div><p></p></div>
        <Html 
            pointerEvents = { false }
        >
            {#if hideTooltip !== true}
                <Tooltip
                    {evt}
                    let:detail
                >

                </Tooltip>
            {/if}
        </Html>
        <Legend />
    </LayerCake>
</figure>



<style>
    figure {
        display: block;
        position: relative;
        width: 100%;
        height: 80vh;
        min-height: 420px;
        margin: 0;
        user-select: none;
    }

    figure > * {
        display: block;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        overflow: hidden;
    }
</style>