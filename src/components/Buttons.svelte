<script>
    import metrics from "../data/metrics"

    // if html not an array, there will be two repeated cost of living label, because contenteditable, Actual dollars button is overwritten
    // export let html = []
    export let clicked_type
    
</script>

<div class = "buttons">
    {#each metrics as {label, key}, i}
        <h4 
            id = {key}
            on:click = {element => {
                clicked_type = metrics[i].label
            }}
        >
            {label}
        </h4>
    {/each}
</div>

<style>
    h4 {
  text-decoration: underline;
}
</style>
