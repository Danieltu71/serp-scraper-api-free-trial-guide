# How to make the most of your SERP Scraper API free trial?

SERP Scraper API by Oxylabs is a public data scraper API tailored to retrieve real-time localized search results data. In this tutorial, we’ll show how to get the most use out of a one-week free trial and help you decide whether this scraping solution serves your business’s needs.

This guide will walk you through setting up Oxylabs’ SERP Scraper API from scratch. Configuring it with a search phrase of your choice will give a good grasp of the data quality, ease of integration, and whether this product is right for you. We will interact with the SERP Scraper API using Python. For more programming languages and more complex examples, visit our [documentation](https://developers.oxylabs.io/scraper-apis/serp-scraper-api). 

If you have discovered this tutorial before visiting our website, you can get a free trial by visiting the [SERP Scraper API](https://oxylabs.io/products/scraper-api/serp) page and filling in the form.

<br>
<img src="Screenshot 2022-08-17 at 17.10.03.png" width="400">

Shortly after, you will receive an email with your username and password. You will need these API user credentials to start using the SERP Scraper API.

<img src="Screenshot 2022-08-17 at 17.11.43.png" width="400">
<br>

## Setting up SERP Scraper API

Now, let’s get into the concrete steps of integrating SERP Scraper API:

1. Open up your IDE (integrated development environment).
2. Insert the credentials you received in your email:

```python
import requests

username = 'username'
password = 'password'
```

3. Define the ‘source’ and enter your preferred ‘query’. In this example we will use ‘Best video games of all time’ as our search phrase.  

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time'
}
```

4. Post Payload to the endpoint as per the example below: [](https://realtime.oxylabs.io/v1/queries)

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))
```

5. As SERP Scraper API delivers a response in JSON, we need to access the ‘content’ key:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']
```

6. After this, we write HTML into the file:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

After running the basic code, try adding parameters to retrieve more specified data. 

7. You can set up geo-location parameters that will help you collect geo-restricted data:

```python
'geo-location': 'New York,New York,United States'
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time',
  'geo-location': 'New York,New York,United States'
}
 
response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
 ```
 
 8. If you want to receive search results as if you’d be visiting the search engine using a specific device, you can add `user_agent_type` parameter. For this example we will set it to `mobile`. 

```python 
'user_agent_type': 'mobile'
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time',
  'geo-location': 'New York,New York,United States',
  'user_agent_type': 'mobile'
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

9. To receive structured data, you can add a `parse` parameter and set it to `true`:

```python
"parser_type": "ecommerce_product",
"parse": true
```

### Example:

```python
import requests

username = 'username'
password = 'password'

payload = {
  'source': 'google_search', #here we define source
  'query': 'Best video games of all time',
  'geo-location': 'New York,New York,United States',
  'user_agent_type': 'mobile',
  'parse': true
}

response = requests.post('https://realtime.oxylabs.io/v1/queries', json = payload, auth = (username, password))

html_content = response.json()['results'][0]['content']

with open ('scraped_website.html', 'w') as output:
  output.write(html_content)
```

And this is it - now you know how to set up SERP Scraper API and use it to your advantage. 

## Conclusion

As you can see from this detailed example, SERP Scraper API is easy to integrate, but also it is packed with lots of valuable features. [Get in touch](https://oxy.yt/LrYs) with our sales team to further discuss your use case and find available targets for SERP Scraper API.

