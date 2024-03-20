<script>
    /* as while developing was found out that impossible to realize multiple charts at the same page withchart.js/auto 
    for this reason was decided to create second chart with svelte-chartjs library (with future changing first chart to the same library)*/
    import { Bar } from "svelte-chartjs";

    // exaple of dataset
    let rawData = [
        { point: "0KB", students: 0 },
        { point: "100KB", students: 2 },
        { point: "200KB", students: 4 },
        { point: "300KB", students: 6 },
        { point: "400KB", students: 8 },
        { point: "500KB", students: 0 },
        { point: "600KB", students: 2 },
        { point: "700KB", students: 4 },
        { point: "800KB", students: 6 },
        { point: "900KB", students: 18 },
        { point: "1MB", students: 10 },
        { point: "1.1MB", students: 3 },
        { point: "1.2MB", students: 14 },
        { point: "1.3MB", students: 19 },
        { point: "1.4MB", students: 22 },
        { point: "1.5MB", students: 15 },
        { point: "1.6MB", students: 18 },
        { point: "1.7MB", students: 11 },
        { point: "1.8MB", students: 4 },
        { point: "1.9MB", students: 7 },
        { point: "2MB", students: 48 },
        { point: "2.1MB", students: 42 },
        { point: "2.2MB", students: 8 },
        { point: "2.3MB", students: 36 },
        { point: "2.4MB", students: 8 },
        { point: "2.5MB", students: 0 },
        { point: "2.6MB", students: 2 },
        { point: "2.7MB", students: 4 },
        { point: "2.8MB", students: 6 },
        { point: "2.9MB", students: 8 },
        { point: "3MB", students: 6 },
        { point: "3.1MB", students: 10 },
        { point: "3.2MB", students: 10 },
        { point: "3.3MB", students: 30 },
        { point: "3.4MB", students: 34 },
        { point: "3.5MB", students: 20 },
        { point: "3.6MB", students: 12 },
        { point: "3.7MB", students: 3 },
        { point: "3.8MB", students: 5 },
        { point: "3.9MB", students: 10 },
        { point: "4MB", students: 45 },
        { point: "4.1MB", students: 11 },
        { point: "4.2MB", students: 2 },
        { point: "4.3MB", students: 13 },
        { point: "4.4MB", students: 4 },
        { point: "4.5MB", students: 20 },
        { point: "4.6MB", students: 20 },
        { point: "4.7MB", students: 9 },
        { point: "4.8MB", students: 7 },
        { point: "4.9MB", students: 10 },
        { point: "5MB", students: 40 },
    ];

    // initial data structure required by svelte-chartjs for rendering the chart. 
    // includes labels for the x-axis and a dataset for the y-axis values.
    let data = {
        labels: rawData.map((item) => item.point),
        datasets: [
            {
                label: "Number of Students",
                backgroundColor: "#E2E4E5",
                data: rawData.map((item) => item.students),
            },
        ],
    };

    // options for configuring the appearance and behavior of the chart
    let options = {
        responsive: true,
        scales: {
            y: {
                beginAtZero: true,
                grid: {
                    display: false,
                },
                ticks: {
                    display: false,
                },
            },
            x: {
                grid: {
                    display: false,
                },
                afterBuildTicks: function (axis) {
                    let ticks = axis.ticks;
                    if (ticks.length > 1) {
                        axis.ticks = [ticks[0], ticks[ticks.length - 1]];
                    }
                },
                maxRotation: 0,
                minRotation: 0,
            },
        },
        plugins: {
            legend: {
                display: false,
            },
            tooltip: {
                yAlign: "bottom",
                backgroundColor: "transparent",
                bodyColor: "black",
                titleColor: "black",
                titleAlign: "center",
                bodyAlign: "center",
                displayColors: false,
                callbacks: {
                    title: function () {
                        return "";
                    },
                    label: function (context) {
                        return `${context.parsed.y}`;
                    },
                },
            },
        },
    };

    // function to update the chart's data by columnCount
    // ! simplified example at the real chart this function should grouped data
    // ! right now this function just takes first n entities
    export function updateChart(columnCount) {
        const stepSize = Math.ceil(rawData.length / columnCount);
        const newData = [];
        for (let i = 0; i < rawData.length; i += stepSize) {
            newData.push(rawData[i]);
        }
        data = {
            labels: newData.map((item) => item.point),
            datasets: [
                {
                    label: "Number of Students",
                    backgroundColor: "#E2E4E5",
                    data: newData.map((item) => item.students),
                },
            ],
        };
    }

    updateChart(50);
</script>

<div>
    <Bar {data} {options} />
</div>
