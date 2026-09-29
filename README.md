# How I Choose a Chart for a Small Spreadsheet

Charttoolbox began as a heatmap generator. As I added more chart types, I kept running into the same problem: making a chart is often easier than deciding which chart answers the question.

A small spreadsheet rarely needs a full dashboard. But choosing the first chart in a menu can hide the story in the data. Here is the short decision guide I now use, along with three fictional CSV examples you can copy and test.

## Start with the question, not the chart

| What do you want to see? | Use | Data shape |
| --- | --- | --- |
| Change over time | Line chart | Date or ordered label + numeric series |
| Differences between categories | Bar chart | Category + one or more numeric series |
| Parts of one complete whole | Pie or donut chart | Category + non-negative value |
| A relationship between two measurements | Scatter plot | Numeric X + numeric Y |
| The distribution of raw measurements | Histogram | One numeric column of observations |
| Patterns across rows and columns | Heatmap | Labeled matrix or X/Y/value table |
| Pairwise linear relationships | Correlation matrix | Several numeric columns of observations |

These choices are about the *question*, not just the file format. For example, a bar chart compares named categories; a histogram groups raw numeric observations into intervals. They may look similar, but they answer different questions.

## Example 1: Two sales series

This fictional table has a date and two values measured in the same unit:

~~~csv
Month,Online sales,Store sales
2026-01-01,120,96
2026-02-01,132,102
2026-03-01,128,110
2026-04-01,151,115
2026-05-01,164,126
2026-06-01,179,139
~~~

Use a **line chart** if you want to follow how each channel changes over time. Use a **grouped bar chart** if the main task is comparing online and store sales month by month. A **heatmap** can help you scan the whole month-by-channel table for high and low values.

The input is the same. The question changes the chart.

![Line chart of fictional monthly online and store sales](images/line-chart.png)

## Example 2: Shares of one budget

~~~csv
Channel,Budget
Search,420
Social,240
Email,180
Events,160
~~~

This fictional budget totals 1,000. A **pie or donut chart** can show the four shares: 42%, 24%, 18%, and 16%. If your reader needs to compare two nearly equal categories precisely, use bars instead.

![Bar chart comparing the four fictional channel budgets](images/bar-chart.png)

A pie chart only works when the categories are parts of the *same whole*. Independent conversion rates, for example, should not be added together to make a pie.

## Example 3: Two measurements per campaign

~~~csv
Campaign,Ad spend,Sign-ups
A,100,12
B,140,18
C,180,17
D,220,29
E,260,34
F,300,31
~~~

Choose a **scatter plot** to inspect ad spend against sign-ups, with one point per campaign. You can also calculate a **correlation matrix** from the two numeric columns, but a correlation coefficient does not establish causation. With only six fictional observations, this example demonstrates the workflow—not a reliable marketing conclusion.

![Scatter plot of fictional campaign ad spend and sign-ups](images/scatter-plot.png)

## From table to export

I use [Charttoolbox](https://www.charttoolbox.com/) for these small, one-off tasks. It accepts CSV, TSV, XLS/XLSX, or cells pasted from a spreadsheet. After importing, I check the detected fields rather than assuming the first guess is correct. Then I adjust the title and presentation, and export a PNG or SVG.

The spreadsheet contents are processed in the browser rather than uploaded to Charttoolbox for chart generation. Optional site analytics loads only with consent and does not receive the table contents. There is no saved cloud project, so keep the source spreadsheet and download the finished chart before closing the page.

This is not meant to replace a BI dashboard or statistical review. It is a quicker path from a small table to a chart you can inspect, correct, and use in a report.

If you try any of the fictional examples, I would be interested to know where the chart choice or field selection still feels unclear.

*Disclosure: I used AI assistance to prepare this article.*
