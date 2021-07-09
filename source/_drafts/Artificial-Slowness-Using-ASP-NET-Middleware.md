---
title: Artificial Slowness Using ASP.NET Middleware
tags:
- asp.net core
- react
---
While writing some React stuff today, I added in a progress spinner to indicate activity during an API call. Everything built and ran fine, but I had a problem: I was running the backend locally, and I only had a handful of entries in my local database. There was virtually no time between making the API call and receiving a response. I couldn't even see the progress spinner pop up.

This isn't a major problem, becuase it's very easy to add an artificial lag to the API logic, or even in the frontend itself. But I thought it would be more useful in the long term to have the ability to easily introduce a short delay for an endpoint, or even the whole API.

This turns out to be relatively simple to do with ASP.NET middleware.

# The Frontend
For this technique, there's nothing special to do in the frontend. Here's an example of a rudimentary loading indicator, taken from the [dotnet-cli React template](https://docs.microsoft.com/en-us/aspnet/core/client-side/spa/react?view=aspnetcore-5.0&tabs=visual-studio):

```
    render() {
        let contents = this.state.loading
            ? <p><em>Loading...</em></p>
            : FetchData.renderForecastsTable(this.state.forecasts);

        return (
            <div>
                <h1 id="tabelLabel" >Weather forecast</h1>
                <p>This component demonstrates fetching data from the server.</p>
                {contents}
            </div>
        );
    }

    async populateWeatherData() {
        const response = await fetch('weatherforecast');
        const data = await response.json();
        this.setState({ forecasts: data, loading: false });
    }
```

# The Backend

