# How to Pass JSON Arrays to a Syncfusion Blazor Chart

## Overview

This sample demonstrates how to load chart data from a JSON file and display it in a Syncfusion [Blazor Charts](https://www.syncfusion.com/blazor-components/blazor-charts). The application retrieves JSON data using `HttpClient`, deserializes it into a strongly typed model, and binds the resulting collection to a chart series.

This approach is useful when chart data is stored in external JSON files or provided through web APIs. By converting JSON content into a .NET model, the chart can efficiently consume and visualize the data while maintaining strong typing and IntelliSense support.

## Key Features

- Uses `Http.GetFromJsonAsync(...)` to load JSON data.
- Uses `NavigationManager.BaseUri` to resolve the JSON file location.
- Defines a strongly typed `ChartData` model with:
  - `X`
  - `High`
  - `Low`
- Stores deserialized records in a `ChartData[]` collection.
- Loads data during `OnInitializedAsync()`.
- Binds the JSON-derived collection to a Blazor chart series.
- Demonstrates rendering a Range Step Area chart from external JSON data.

## Prerequisites

- [Visual Studio 2022](https://visualstudio.microsoft.com/vs/) or [Visual Studio Code](https://code.visualstudio.com/)
- [.NET SDK](https://dotnet.microsoft.com/en-us/download/dotnet) compatible with the project's target framework

## How to Run the Project
 
**Visual Studio 2022**
 
1. Clone the repository.
2. Open Visual Studio 2022.
3. Select **Open a project or solution**.
4. Browse to the project file:
 
`ChartWithJSONdata.csproj`
 
5. Restore NuGet packages if prompted.
6. Build the project.
7. Run the application using `Ctrl+F5`.

**Visual Studio Code**

1. Clone the repository.
2. Open the repository folder in Visual Studio Code.
3. Open the integrated terminal.
4. Navigate to the project directory:

```bash
cd ChartWithJSONdata
```

5. Restore packages:

```bash
dotnet restore
```

6. Run the application:

```bash
dotnet run
```

7. Open the URL displayed in the terminal.

## Project Structure

`ChartWithJSONdata/Pages/Index.razor` - Hosts the chart, loads JSON data, defines the `ChartData` model, and binds the collection to the chart series.

## Support and Feedback

- For general product questions, visit the [Syncfusion Community Forum](https://www.syncfusion.com/forums) or [Syncfusion Support](https://www.syncfusion.com/support).
- To report an issue specific to this sample, open a GitHub issue in this repository.
- For feature documentation, see the Syncfusion Blazor Chart documentation: https://help.syncfusion.com/chart-sdk/blazor/charts/getting-started

## License

This is a Syncfusion sample project provided to demonstrate product usage. Review the [Syncfusion license terms](https://www.syncfusion.com/sales/pricing?category=ui-components) before using Syncfusion components in your own applications.