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

conn.request("GET", "/search?query=Marketing%20manager%20in%20Mexico&page=4&num_pages=20", headers=headers)

res = conn.getresponse()
data = res.read()

print(data.decode("utf-8"))
```
