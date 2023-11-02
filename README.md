# how-to-pass-JSON-arrays-to-Blazor-chart
**JSON** data cannot be bound directly into [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts), so we should deserialize the JSON data to a bindable format.

The following steps explain  how to pass JSON data to [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts).

**Step 1**: Import the following namespace in the razor file and store the JSON file inside wwwroot folder.

```cshtml

@inject NavigationManager NavigationManager
@inject HttpClient Http
@using System.Net.Http.Json

```



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
 
**JSON** data cannot be bound directly into [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts),  so we should deserialize the JSON data to a bindable format. 
The following steps explain  how to pass JSON data to [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts).
**Step 1**: Import the following namespace in the razor file and store the JSON file inside wwwroot folder.


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
        ChartPoints = new ChartData[] { };
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
    <ChartArea>
        <ChartAreaBorder Width="0"></ChartAreaBorder>
    </ChartArea>
    <ChartTooltipSettings Enable="true" Format="Temperature : <b>${point.low} - ${point.high}</b>" Shared="true"></ChartTooltipSettings>
    <ChartPrimaryXAxis ValueType="Syncfusion.Blazor.Charts.ValueType.DateTime" Format="dd MMM">
        <ChartAxisMajorGridLines Width="0"/>
    </ChartPrimaryXAxis>
    <ChartPrimaryYAxis LabelFormat="{value}˚C" Interval="5" Minimum="-5" Maximum="25">
        <ChartAxisLineStyle Width="0"></ChartAxisLineStyle>
        <ChartAxisMajorTickLines Width="0"/>
    </ChartPrimaryYAxis>
    <ChartSeriesCollection>
    <ChartSeries DataSource="@ChartPoints" XName="X" High="High" Low="Low"  Opacity="0.5" Type="ChartSeriesType.RangeStepArea">
            <ChartMarker Visible="false"></ChartMarker>                 
        </ChartSeries>
    </ChartSeriesCollection>
    <ChartLegendSettings Visible="false"/>
</SfChart>

@code{

    public string BorderColor { get; set; }    
    public ChartData[] ChartPoints { get; set; }

    protected async override Task OnInitializedAsync()
    {
        ChartPoints = new ChartData[] { };
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

![](https://github.com/SyncfusionExamples/how-to-pass-JSON-arrays-to-Blazor-chart/blob/main/)

**Conclusion**
I hope you enjoyed learning how to customize Axis range in Blazor Chart Component.
You can refer to our Blazor Chart feature tour page to know about its other groundbreaking feature representations and documentation, and how to quickly get started for configuration specifications. You can also explore our Blazor Chart example to understand how to create and manipulate data.
For current customers, you can check out our components from the License and Downloads page. If you are new to Syncfusion, you can try our 30-day free trial to check out our other controls.
If you have any queries or require clarifications, please let us know in the comments section below. You can also contact us through our support forums, Direct-Trac, or feedback portal. We are always happy to assist you!



