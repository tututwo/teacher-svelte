
<div class = "legend-container">
    <ul class="legend">
        <li>2010<span class="arrow years"></span>2016</li>
        <li><span class="arrow increase"></span>Pay increased</li>
        <li><span class="arrow decrease"></span>Pay decreased</li>
        <li><span class="walkout-bar"></span><span class="walkout-text">Walkouts</span></li>
    </ul>
</div>
<style>


    .legend-container {
        position:relative;
        text-align: center;
    }
    .legend {
        position: absolute;
        color: #696969;
        background-color: #fff;
        font-family: "Liberation Mono",monospace;
        padding-right: 10px;
        top: 20px;
        font-size: 1rem;
        left: 10%;
    }
    @media (max-width: 600px) {
        .legend {
            font-size: 0.7rem;
            left: 0
        }
    }
    .legend li {
        margin: 8px 0 8px 0;
        list-style: none;
    }
    .legend .arrow.years {
        background: url(https://graphics.axios.com/2018-03-23-teacher-salary/img/arrow-years.svg);
        transform: rotate(
    180deg);
        margin-left: 3px;
    }
    .legend .arrow {
        background-repeat: none;
        display: inline-block;
        margin-right: 3px;
        height: 10px;
        width: 20px;
    }

    .legend .arrow.increase {
        background: url(https://graphics.axios.com/2018-03-23-teacher-salary/img/arrow-increase.svg);
        -webkit-transform: rotate(
    180deg);
        transform: rotate(
    180deg);
    }
    .legend .arrow.decrease {
        background: url(https://graphics.axios.com/2018-03-23-teacher-salary/img/arrow-decrease.svg);
    }   
    .legend .walkout-bar {
        background-color: #ebe2d7;
        position: relative;
        top: 4px;
        left: 1px;
        height: 10px;
        width: 19px;
        float:left
    }

    .legend .walkout-text {
       margin-left: -2.7em;
    }
</style>