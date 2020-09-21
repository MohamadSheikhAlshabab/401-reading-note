# Readings: Django CRUD and Forms [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read22.md)

## Django Tutorial Part 9: Working with forms:

  - __Overview__: 
    - An HTML Form is a group of one or more fields/widgets on a web page, which can be used to collect information from users for submission to a server.
    - Forms are a flexible mechanism for collecting user input because there are suitable widgets for entering many different types of data, including text boxes, checkboxes, radio buttons, date pickers and so on.
    - Forms are also a relatively secure way of sharing data with the server, as they allow us to send data in POST requests with cross-site request forgery protection.
 
 - __HTML Forms__:
   - The form is defined in HTML as a collection of elements inside form tags, containing at least one input element of type="submit".
   - The form attributes define the HTTP method used to send the data and the destination of the data on the server (action):

      - action: The resource/URL where data is to be sent for processing when the form is submitted. If this is not set (or set to an empty string), then the form will be submitted back to the current page URL.
      - method: 
        - The HTTP method used to send the data: post or get.
        - The POST method should always be used if the data is going to result in a change to the server's database because this can be made more resistant to cross-site forgery request attacks.
        - The GET method should only be used for forms that don't change user data (e.g. a search form). It is recommended for when you want to be able to bookmark or share the URL.
   
   - __Django form handling process__:
     - the view gets a request, performs any actions required including reading data from the models, then generates and returns an HTML page.
     - ![img](https://mdn.mozillademos.org/files/14205/Form%20Handling%20-%20Standard.png)
     -  the main things that Django's form handling does are:

       - 1 - Display the default form the first time it is requested by the user.
            - The form may contain blank fields (e.g. if you're creating a new record), or it may be pre-populated with initial values (e.g. if you are changing a record, or have useful default initial values).
            - The form is referred to as unbound at this point, because it isn't associated with any user-entered data (though it may have initial values).
       - 2 -  Receive data from a submit request and bind it to the form.
            - Binding data to the form means that the user-entered data and any errors are available when we need to redisplay the form.
       - 3 - Clean and validate the data.
            - Cleaning the data performs sanitization of the input (e.g. removing invalid characters that might be used to send malicious content to the server) and converts them into consistent Python types.
            - Validation checks that the values are appropriate for the field (e.g. are in the right date range, aren't too short or too long, etc.)
       - 4 - If any data is invalid, re-display the form, this time with any user populated values and error messages for the problem fields.
       - 5 - If all data is valid, perform required actions (e.g. save the data, send an email, return the result of a search, upload a file, etc.)
       - 6 - Once all actions are complete, redirect the user to another page.
       
---
## Django Tutorial Part 5: Creating our home page:
  - __Overview__:
      - The first thing we need to do is determine what information we want to display in our pages, and define the URLs to use for returning those resources.
      - Then we'll create a URL mapper, views, and templates to display the pages. 

    - the main components we'll create are:
      - URL mappers to forward the supported URLs (and any information encoded in the URLs) to the appropriate view functions.
      - View functions to get the requested data from the models, create HTML pages that display the data, and return the pages to the user to view in the browser.
      - Templates to use when rendering data in the views.
      - ![img](https://mdn.mozillademos.org/files/13931/basic-django.png)
      
  - __Defining the resource URLs__:
     - The URLs that we'll need for our pages are:
          - catalog/ — The home (index) page.
          - catalog/books/ — A list of all books.
          - catalog/authors/ — A list of all authors.
          - catalog/book/<id> — The detail view for a particular book, with a field primary key of <id> (the default). For example, the URL for the third book added to the list will be /catalog/book/3.
          - catalog/author/<id> — The detail view for the specific author with a primary key field of <id>. For example, the URL for the 11th author added to the list will be  /catalog/author/11.
      
---
