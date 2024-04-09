---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults
title: Homework 8 IS445
---

For the first plot, it shows the distribution of license types by states. The interactive feature allows the user to switch between the different states. The x-axis is the License type, while the y-axis has the number of the different licenses. The color was chosen to reflect the different license types to clearly show the distributions of these licenses. Furthermore, the tooltip uses the state, license type and the number of licneses. In terms of properties, I wanted the height and width of the graph to stay constant instead of changing when a new state is selected. They are kept at a constant width of 800 and height of 400. The state select is the dropdown box that allows the user to choose a specific state to look at. The selection within the dropdown box are all the states available in the dataset. 

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Distribution of License Types by State</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js@3.9.1/dist/chart.min.js"></script>
</head>
<body>
  <h1>Distribution of License Types by State</h1>
  <div id="myChartContainer"></div>
  <script>
    const chartData = {
      labels: [],
      datasets: [{
        label: 'License Count',
        data: [],
        backgroundColor: []
      }]
    };

    // Loop through your JSON data and populate chartData
    const jsonData = JSON.parse('[Replace with your JSON data]'); // Replace with actual JSON data
    jsonData.datasets['data-a8d06f529c9929af5a432d8d0550f02e'].forEach(entry => {
      chartData.labels.push(entry.State);
      chartData.datasets[0].data.push(entry.Count);
      // Add colors based on License Type (replace with your logic)
      chartData.datasets[0].backgroundColor.push('rgba(255, 99, 132, 0.2)'); // Example color
    });

    const ctx = document.getElementById('myChartContainer').getContext('2d');
    const myChart = new Chart(ctx, {
      type: 'bar',
      data: chartData,
      options: {
        scales: {
          yAxes: [{
            ticks: {
              beginAtZero: true
            }
          }]
        }
      }
    });
  </script>
</body>
</html>

For the second plot, it shows the distribution of the types of actions and their number of occurences. The x-axis is the Action, while the y-axis has the number of occurances. The tooltip uses only those variables. For properties, they are set to constant once again at a width of 800 and height of 400. Initially, I was going to make the graph interactive as well allowing the user to choose between the states. This would have allowed the user to see the different type of actions and their number of occurances for indivisual states. However, the dataset did not have enough data for most states outside of Illinois. Only Illinois had more than 10 datasets. I included the interactive version below in the Workbook.ipynb and if you look at other states, there is a notable differnce in the number of data. I concluded that it would be better to have a static plot rather than an interactive one in this case to best showcase the distribution. 
