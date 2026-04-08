# Exemplo de Gantt com o Quickchat

1 - Adicione uma imagem

2 - Cole na propriedade Image:

```powerfx
"https://quickchart.io/chart?c=" & EncodeUrl(
"
{
  type: 'horizontalBar',
  data: {
    labels: ['Part 1', 'Part 2', 'Part 3', 'Part 4', 'Part 5', 'Part 6'],
    datasets: [{
      data: [
        [new Date('2021-02-01'), new Date('2021-05-01')],
        [new Date('2021-05-10'), new Date('2021-07-01')],
        [new Date('2021-04-20'), new Date('2021-11-31')],
        [new Date('2021-08-01'), new Date('2021-09-01')],
        [new Date('2021-02-10'), new Date('2021-07-01')],
        [new Date('2021-07-20'), new Date('2021-11-31')],
      ],
      backgroundColor: ['rgb(255, 99, 132, 1.0)', 'rgba(255, 99, 132, 1.0)', 'rgba(255, 206, 86, 1.0)', 'rgba(255, 206, 86, 1.0)', 'rgba(255, 206, 86, 0.2)', undefined],
    }, ],
  },
  options: {
    legend: {
      display: false
    },
    annotation: {
      annotations: [{
        type: 'line',
        mode: 'vertical',
        scaleID: 'x-axis-0',
        value: new Date('2021-10-30'),
        borderColor: 'red',
        borderWidth: 1,
        label: {
          enabled: true,
          content: 'Deadline',
          position: 'top'
        }
      }]
    },
    scales: {
      xAxes: [{
        position: 'top',
        type: 'time',
        time: {
          unit: 'month'
        },
        ticks: {
          min: new Date('2021-01-01'),
          max: new Date('2022-01-01'),
        }
      }],
    },
  },
}")
```
