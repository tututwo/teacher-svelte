<script>
    import metrics from "../data/metrics"

    // if html not an array, there will be two repeated cost of living label, because contenteditable, Actual dollars button is overwritten
    // export let html = []
    export let clicked_type
</script>

<div class = "buttons">
    <div class="headline-units">Ranked by 2016 salary:</div>

    {#each metrics as {label, key}, i}
        <span 
            id = {key}
            on:click = {element => {
                clicked_type = metrics[i].label
            }}
            class:selected = {clicked_type == metrics[i].label}
        >
            {label}
        </span>
    {/each}
</div>

<style>
    .buttons {
        text-align: center;
        color: #858585;
        /* position:relative */
        margin-bottom: 30px;
    }
    .buttons span {
        display: inline-block;
        line-height: 1.5;
        margin: 0 4px 3px 4px;
        border-bottom: 3px solid #dcdcdc;
        font-family: "Liberation Mono",monospace;
        font-size: 0.9rem;
        text-align: center;
        cursor: pointer;
        
    }
    .buttons .selected {
        border-bottom: 3px solid #696969;
        color:#4a4a4a
    }

    .buttons .headline-units{
        /* position:absolute; */
        display: inline;
        font-size: 1em;
        /* margin: 3px 10px 30px -10.8em; */
        box-sizing: border-box;
    }

    @media (min-width: 600px) {
        .buttons .headline-units {
            display: inline
        }
    }
</style>

