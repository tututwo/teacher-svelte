<script>
    import { tweened } from "svelte/motion"
    import { expoOut } from "svelte/easing";
    import { getContext } from "svelte"

    export let class_sign, Abbr, x1,x2, translatedY,i

    const {yScale, xRange} = getContext('LayerCake')
    
    $: width = $xRange[1]
    $: height = $yScale.bandwidth()
    
    const options = {
        duration: 800,
        delay: i * 2,
        easing: expoOut
    }
    
    const x1Tween = tweened(x1, options)
    const x2Tween = tweened(x2, options)
    const yTween = tweened(translatedY, options)

    $: {
        $x1Tween = x1;
        $x2Tween = x2;
        $yTween = translatedY;
    }
</script>

<g 
    class:negative = {class_sign}
    class = {'state' + " " + Abbr}
    transform = "translate(0, {$yTween})"
    on:mouseover
>
    <rect 
        {width} {height}
    />
    <text
        class = "state-label"
        x = {$x1Tween}
        y = 5
        text-anchor = {class_sign ? "start":"end"}
    >
        <slot/>
    </text>

    <line
        x1 = {$x1Tween}
        y1 = 0
        x2 = {$x2Tween}
        y2 = 0
        stroke-width = 3
        marker-end= {class_sign? "url(#arrow-neg)" : "url(#arrow-pos)"}
    />


</g>

<style>
    .state.negative line {
        stroke: #ff9b5a;
    }
    .state line {
        stroke: #9686f7;
    }
    .state.negative .state-label {
        fill: #ff9b5a;
    }
    
    .state-label {
        fill: #9686f7;
        font-size: 14px;
        font-family: "Liberation Mono",monospace;
        paint-order: stroke;
        stroke: #fff;
        stroke-width: 4px;
        stroke-linecap: round;
        stroke-linejoin: round;
    }

    .state rect{
        opacity: 0;
        pointer-events: all;
    }
    .state:hover rect{
        fill:#dcdcdc;
        opacity: 0.75;
        transform: translateY(-8px);
    }
</style>