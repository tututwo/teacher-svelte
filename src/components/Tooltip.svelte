<script>
    import { format } from "d3-format"

    export let evt
    const num_format = format("$,.5")
</script>

{#if evt.detail}
    <div
        class = "tooltip"
        style = "
            top: {evt.detail.e.layerY}px;
            left: {evt.detail.e.layerX}px
        "
    >
        <!-- <slot detail = {evt.detail}></slot> -->
        {#each Object.entries(evt.detail.props) as [key, value], i}
            {#if i == 0}
                <h4 class = "header">
                    {value}   
                </h4>
            {:else if i == 1 || i == 4}
               <div class = "blank"></div>
            {:else if i == 2}
            <div>
                <span class = 'year'>2010 </span>
                <span class = "salary">{num_format(value)}</span>
            </div>
            {:else}
            <div>
                <span class = "year">2016 </span>
                <span class = "salary">{num_format(value)}</span>
            </div>
            {/if}

        {/each}

        <!-- {#each evt.detail.p}

        {/each} -->
    </div> 
{/if}


<style>
    .tooltip {
        position: absolute;
        width: 200px;
        border: 1px solid #ccc;
        font-size: 0.85em;
        font-family: "Liberation Mono",monospace;
        background: rgba(255, 255, 255, 0.85);
        transform: translate(-50%, -100%);
        padding: 5px;
        z-index: 15;
    }
    .tooltip .header {
        color: #4a4a4a;
        font-family: Gordita,Helvetica,Arial,sans-serif;
        font-weight: 600;
        margin-bottom: 8px;
        text-align: left;
    }

    .tooltip .blank {
        margin-bottom: 5px;
        padding-bottom: 5px;
        border-bottom: 1px dotted #ccc;
    }
    .tooltip .year {
        display: inline-block;
        text-align: left;
    }
    .tooltip .salary {
        display: inline-block;
        text-align: right;
    }
</style>