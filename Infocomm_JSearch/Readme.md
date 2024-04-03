# JSearch

Use rapidapi JSearch API:

https://rapidapi.com/letscrape-6bRBa3QguO5/api/jsearch

Following the Python snippet:

```
import http.client

conn = http.client.HTTPSConnection("jsearch.p.rapidapi.com")

headers = {
    'X-RapidAPI-Key': "use-your-api-key",
    'X-RapidAPI-Host': "jsearch.p.rapidapi.com"
}

conn.request("GET", "/search?query=Some%20occupation%20in%20Mexico&page=4&num_pages=20", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```

That creates a JSON like variable in `data` with the following structure:

```
{
    "status": "OK",
    "request_id": "1fd6f328-9ca3-49ee-b823-2c69228f069a",
    "parameters": {
        "query": "some occupation in mexico",
        "page": 1,
        "num_pages": 1
    },
    "data": [
        {
         ... some job post details ...
        }
    ]
```

We then convert it to a Panda's Dataframe:

```
import pandas as pd
import json

# Parse the JSON string into a Python dictionary
data_dict = json.loads(data.decode("utf-8"))

# Convert the 'data' section of the dictionary into a DataFrame
df = pd.DataFrame(data_dict['data'])
```

`images/dataframeexample.png`

