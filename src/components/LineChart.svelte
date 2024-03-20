<script>
    import { onMount } from "svelte";
    import Chart from "chart.js/auto";
    import "chartjs-adapter-date-fns";

    // hold the Chart.js instance
    let chart;

    // possible datasets
    const rawData = [
        {
            date: "2023-06-10",
            task: "social-network",
            points: "30",
            currPoints: "230",
        },
        {
            date: "2023-10-20",
            task: "email-marketing",
            points: "20",
            currPoints: "250",
        },
        {
            date: "2023-12-10",
            task: "social-network",
            points: "300",
            currPoints: "530",
        },
        {
            date: "2024-02-20",
            task: "email-marketing",
            points: "200",
            currPoints: "730",
        },
        {
            date: "2024-03-15",
            task: "content-creation",
            points: "500",
            currPoints: "1230",
        },
    ];

    const rawData2 = [
        {
            date: "2024-02-11",
            task: "social-network",
            points: "10",
            currPoints: "100",
        },
        {
            date: "2024-02-28",
            task: "email-marketing",
            points: "10",
            currPoints: "110",
        },
        {
            date: "2024-03-10",
            task: "content-creation",
            points: "10",
            currPoints: "1000",
        },
    ];

    // generates an array of date strings between two dates, inclusive
    // function logic to populate an array with dates from startDate to endDate
    function generateDateLabels(startDate, endDate) {
        const dateArray = [];
        let currentDate = new Date(startDate);

        while (currentDate <= endDate) {
            dateArray.push(currentDate.toISOString().split("T")[0]); // Format: YYYY-MM-DD
            currentDate.setDate(currentDate.getDate() + 1); // Increment day
        }

        return dateArray;
    }

    // converts raw data into a format suitable for Chart.js, filtering and processing the data as needed
    // function logic to transform rawData into a dataset for the chart
    function convertToDataset(rawData, startDate, endDate) {
        // Ensure rawData is sorted by date in ascending order
        rawData.sort((a, b) => new Date(a.date) - new Date(b.date));

        // Find the last data point before the startDate
        let lastValueBeforeStart = 0;
        for (let i = rawData.length - 1; i >= 0; i--) {
            if (new Date(rawData[i].date) < startDate) {
                lastValueBeforeStart = parseInt(rawData[i].currPoints, 10);
                break; // Exit the loop once the last data point before startDate is found
            }
        }

        // Filter rawData to include only points within the specified time range
        const filteredData = rawData.filter((dataPoint) => {
            const dataDate = new Date(dataPoint.date);
            return dataDate >= startDate && dataDate <= endDate;
        });

        // Initialize the dataset with the first point at startDate using lastValueBeforeStart
        let dataset = [
            {
                x: startDate.toISOString().split("T")[0],
                y: lastValueBeforeStart,
            },
        ];

        // Add filtered data points to the dataset
        filteredData.forEach((dataPoint) => {
            dataset.push({
                x: dataPoint.date,
                y: parseInt(dataPoint.currPoints, 10),
            });
        });

        // Ensure the last data point extends to endDate with the last point's value
        const lastPointValue = dataset[dataset.length - 1].y;
        const endDateStr = endDate.toISOString().split("T")[0];
        dataset.push({ x: endDateStr, y: lastPointValue });

        return dataset;
    }

    onMount(() => {
        // initializes the chart instance when the component is mounted in the DOM
        const ctx = document.getElementById("progressChart").getContext("2d");

        // define the start and end dates for the chart's X-axis
        const endDate = new Date();
        const startDate = new Date(endDate);
        startDate.setMonth(endDate.getMonth() - 1);

        // labels for the X-axis
        const labels = generateDateLabels(startDate, endDate);

        // datasets convertation
        const dataset1 = convertToDataset(rawData, startDate, endDate);
        const dataset2 = convertToDataset(rawData2, startDate, endDate);

        // create the Chart.js instance with the specified configuration
        chart = new Chart(ctx, {
            type: "line",
            data: {
                labels: labels,
                // array of datasets to plot on the chart
                datasets: [
                    {
                        label: "Cumulative Points",
                        data: dataset1,
                        borderColor: "#696C72",
                        pointBackgroundColor: "#696C72",
                        borderWidth: 2,
                        fill: false,
                        pointRadius: 3,
                        pointHoverRadius: 6,
                        pointHoverBorderColor: "#C7D100",
                    },
                    {
                        label: "Progress",
                        data: dataset2,
                        borderColor: "#E2E4E5",
                        borderWidth: 2,
                        fill: false,
                        pointRadius: -1,
                    },
                ],
            },
            options: {
                // Chart.js configuration options for responsiveness, axis types and formats, tooltips, etc.
                responsive: true,
                scales: {
                    x: {
                        type: "time",
                        time: {
                            unit: "day",
                            tooltipFormat: "MMM dd, yyyy",
                        },
                        ticks: {
                            autoSkip: true,
                            maxTicksLimit: 20,
                            display: false,
                        },
                        grid: {
                            display: false,
                        },
                    },
                    y: {
                        beginAtZero: true,
                        grid: {
                            display: false,
                        },
                        ticks: {
                            callback: function (value, index, values) {
                                // Convert KB or MB to human-readable format
                                if (value >= 1024) {
                                    return (value / 1024).toFixed(1) + "MB";
                                } else {
                                    return value + "KB";
                                }
                            },
                        },
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
                            title: function (tooltipItems) {
                                return 'Task Name';
                            },
                            label: function (context) {
                                return `${(context.parsed.y >= 1024 ? `${(context.parsed.y / 1024).toFixed(1)}MB` : `${context.parsed.y}KB`)}`;
                            },
                        },
                    },
                },
            },
        });
    });

    // function to update the chart with a new time range based on the number of months provided
    export function updateChart(months) {
        const endDate = new Date();
        const startDate = new Date(endDate);
        startDate.setMonth(endDate.getMonth() - months);

        const dataset1 = convertToDataset(rawData, startDate, endDate, 0); // Regenerate dataset1
        const dataset2 = convertToDataset(rawData2, startDate, endDate, 0); // Regenerate dataset2

        // update the chart's data
        chart.data.datasets[0].data = dataset1;
        chart.data.datasets[1].data = dataset2;
        chart.options.scales.x.min = startDate.toISOString().split("T")[0];
        chart.options.scales.x.max = endDate.toISOString().split("T")[0];

        // refresh the chart to show the updated data
        chart.update();
    }
</script>

<canvas
    id="progressChart"
></canvas>