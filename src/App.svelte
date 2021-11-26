<script>
	import Chart from "./Chart.svelte"
</script>

<main>
	<section>
		<h1 class = "headline">Change in teacher salary, 2010–20</h1>
		<p>showing changes in the past decade</p>
	</section>

	<Chart/>
</main>

<style>
	main {
		font-family: "Inter", sans-serif;
		padding: 0 1em;
		max-width: 50em;
		margin: 0 auto;
  	}

	.headline {
    font-family: Gordita,Helvetica,Arial,sans-serif;
    font-size: 25px;
    line-height: 25px;
    font-weight: 500;
    color: #4a4a4a;
    margin-bottom: 10px;
	
	}

	section h1 {
    display: block;
    margin-block-start: 1.33em;
    margin-block-end: 1.33em;
    margin-inline-start: 0px;
    margin-inline-end: 0px;
    font-weight: bold;
	text-align: center;
	}
</style>