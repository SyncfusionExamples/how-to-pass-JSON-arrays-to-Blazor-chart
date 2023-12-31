# How-to-pass-JSON-arrays-to-Blazor-chart

This article explains how to bind the values from JSON array into blazor chart.

**Creating Blazor RangeStepArea chart using JSON array**
 
**JSON** data cannot be bound directly into [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts), Therefore, it is necessary to convert the JSON data into a format that can be easily bound.

The following steps explain  how to pass JSON data to [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts).

**Step 1**: Import and inject the following namespace in the razor file and store the JSON file inside wwwroot folder.

```cshtml

@inject NavigationManager NavigationManager
@inject HttpClient Http
@using System.Net.Http.Json

```
**Step 2**: Create a Class and Array to store the JSON data as below.

```cshtml

public class ChartData
{
    public string X { get; set; }
    public double High { get; set; }
    public double Low { get; set; }
}

public ChartData[] ChartPoints { get; set; }

```

**Step 3**: Get data from JSON file and get stored in Array using GetFromJsonAsync method.

```cshtml

protected async override Task OnInitializedAsync()
{     
    ChartPoints = await Http.GetFromJsonAsync<ChartData[]>(NavigationManager.BaseUri + "./range-data.json");
}  

```

**Step 4**: Bind the JSON data stored in ChartPoints to the chart series.

```cshtml

<SfChart>

    <ChartSeriesCollection>
        <ChartSeries DataSource="@ChartPoints" XName="X" High="High" Low="Low"  Opacity="0.5" Type="ChartSeriesType.RangeStepArea">             
        </ChartSeries>
    </ChartSeriesCollection>
 
</SfChart>

```

## Blazor Chart with JSON data:

**Index.razor**

```cshtml

@using Syncfusion.Blazor.Charts
@inject NavigationManager NavigationManager 
@inject HttpClient Http 
@using System.Net.Http.Json
 
<SfChart>    
     
    <ChartPrimaryXAxis ValueType="Syncfusion.Blazor.Charts.ValueType.DateTime" Format="dd MMM">
        <ChartAxisMajorGridLines Width="0"/>
    </ChartPrimaryXAxis>

    <ChartPrimaryYAxis LabelFormat="{value}˚C" Interval="5" Minimum="-5" Maximum="25">
        <ChartAxisLineStyle Width="0"></ChartAxisLineStyle>
        <ChartAxisMajorTickLines Width="0"/>
    </ChartPrimaryYAxis>

    <ChartSeriesCollection>
        <ChartSeries DataSource="@ChartPoints" XName="X" High="High" Low="Low"  Opacity="0.5" Type="ChartSeriesType.RangeStepArea">                             
        </ChartSeries>
    </ChartSeriesCollection>     

</SfChart>

@code{

    public string BorderColor { get; set; }    
    public ChartData[] ChartPoints { get; set; }

    protected async override Task OnInitializedAsync()
    {         
        ChartPoints = await Http.GetFromJsonAsync<ChartData[]>(NavigationManager.BaseUri + "./range-data.json");
    }  

    public class ChartData
    {
        public string X { get; set; }
        public double High { get; set; }
        public double Low { get; set; }
    }
}

```

The following screenshot illustrates the result of RangeStepArea  chart by using JSON data.

**Output:**

![](/Json-data-binding.png)

**Conclusion**

I hope you enjoyed learning how to pass JSON array in Blazor Chart Component.

You can refer to our [Blazor Chart feature tour](https://www.syncfusion.com/blazor-components/blazor-charts) page to know about its other groundbreaking feature representations and [documentation](https://blazor.syncfusion.com/documentation/chart/getting-started), and how to quickly get started for configuration specifications. You can also explore our [Blazor Chart example](https://blazor.syncfusion.com/demos/chart/line?theme=bootstrap5) to understand how to create and manipulate data.

For current customers, you can check out our components from the [License and Downloads](https://www.syncfusion.com/sales/teamlicense) page. If you are new to Syncfusion, you can try our 30-day [free trial](https://www.syncfusion.com/downloads/blazor) to check out our other controls.

If you have any queries or require clarifications, please let us know in the comments section below. You can also contact us through our [support forums](https://www.syncfusion.com/forums), [support portal](https://support.syncfusion.com/create), or [feedback portal](https://www.syncfusion.com/feedback/blazor-components?control=charts). We are always happy to assist you!



