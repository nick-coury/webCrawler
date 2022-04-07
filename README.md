# 3700_Crawler

## Approach

1. Requirements   

We were asked to write our own web crawler to find hidden flags on the FakeBook website. Our crawler needed to stay on the target domain, and only resort to using a defualt server and port if none were given. Our sockets also needed to be wrapped in TLS in order to ensure security.  



2. High Level Code Structure 

``` python
class MyHTMLParser(HTMLParser):
    # This gets all the links we need to process and adds them to pages_to_visit iff they haven't been visited
    def handle_starttag(self, tag, attrs):

    # Handles the finding of flags and adds it to our flags list
    def handle_data(self, data):

class Crawler:
    # The initialization method for the crawler
    def __init__(self, args):

    # Builds the cookie header based on the cookies we have and returns the finished cookie header
    def get_cookie(self): 

    # Returns the status code and stores information about cookies and location (if applicable)
    def parse_http(self, data):

    # Sends a formatted message and processes the response given by the server
    def send_and_handle(self, host, path, message):  
  
    # Creates a GET request and passes it to send_and_handle
    def get_req(self, host, path):  
    
    # Creates a POST request and passes it to send_and_handle
    def post_req(self, host, path, payload):       

    # Handles the login and cookie creation
    def login(self):
    
    # Running method using all above helpers 
    def run(self):      
        
```

3. Implementation 

At a high level, here was our approach: 

- Handle login 
- While collected flags is less than 5 (the target number)
    - Crawl 

## Challenges 

We had a hard time when dealing with the special '\n' and '\r' charachters when formatting messages. By not being able to see the invisible characters, the string concatenation was thrown off. This was a really hard bug to find but was very rewarding once we got it done.  


## Program Features

The program is well documented: every choice is commented with an explanation of what is going on and the data structures/variable types are explicitly stated. Additionally, our code has a couple helper methods that enable more testing such as parser overrides. 

Our code is also well abstracted making further development easier. In the case that any message type added, our code has a framework to support it.

## Testing 

Testing was primarily done with print statments and an outside HTTPS simulator. Print statements were particularly useful in figuring out the formatting isues of our messages. The outside HTTPS simulator was particularly useful in figuring out the content issues of our messages. The use of the IDE's debugger allowed us to see console print statements and variable values at every step of our code. 





