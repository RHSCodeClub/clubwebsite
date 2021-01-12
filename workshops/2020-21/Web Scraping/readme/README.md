
# Workshop 4: Web Scraping
We’ll be learning how to use Python to [scrape the web](https://en.wikipedia.org/wiki/Web_scraping)

### Step 1: Setting up Repl
Before we begin coding, you must set up a text editor. We recommend using repl.it

If you do not have an account already, register 

Once you are logged in, create a new repl with the language “python”

You are now ready to begin coding!


### Step 2: Setting up the Python File
In order for the program to get the information from a website, it needs to request the code from the server. 
To do this, import the request package and the BeautifulSoup Package:
```python
import requests
from bs4 import BeautifulSoup
```
Then you can choose a website to request HTML from:
```python
# Collect and parse from our club website
page = requests.get(“https://rhscode.tech/”) #change this to a different website you like
soup = BeautifulSoup(page.text, 'html.parser')
```


### Step 3: Extracting Page Title

Now you want to extract the page title from the website you selected.  In order to do so, you must use BeautifulSoup to store the title of this page in a variable called page_title: 

```python
page_title = soup.title.text
```

Now that this data was extracted, you must print it out in order to view the collected data: 


```python 
print(page_title)
```


### Step 4: Extracting the head and body

It is equally easy to extract out certain sections too.

You saw that you have to call .text on these to get the string, but you can print them without calling .text too, and it will give you the full markup.



```python
import requests
from bs4 import BeautifulSoup

# Make a request
page = requests.get(“https://rhscode.tech/”)
soup = BeautifulSoup(page.content, 'html.parser')

# Extract title of page
page_title = soup.title

# Extract body of page
page_body = soup.body

# Extract head of page
page_head = soup.head

# print the result
print(page_title, page_head)
```

### Step 5: Selecting elements with BeautifulSoup

Once you have the soup object, you can work with .select on it which is a CSS selector inside BeautifulSoup. 
```python
import requests
from bs4 import BeautifulSoup

# Make a request
page = requests.get(“https://rhscode.tech/”)
soup = BeautifulSoup(page.content, 'html.parser')

# Extract title of page
page_title = soup.title

# Extract body of page
page_body = soup.body

# Extract head of page
page_head = soup.head

# print the result
print(page_title, page_head)

# Extract first <h1>(...)</h1> text
first_h1 = soup.select('h1')[0].text #index 0 
```

### CHALLENGE
Try to extract and print out a list of the names of all the workshops on our club website

Solution will be given at the end of the meeting




