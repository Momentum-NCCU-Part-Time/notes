# Django Front End 

Thinking back to the Instagram example, we need a way to display the data in the database to the user in a meaningful way, 
like showing posts in their feed. Each page in a Django app requires three connected parts to work together:
  - a url
  - a view
  - a template

## Templates

Django applications need a `templates` directory, and you have two choices where to put it. You can either do as you did in the 
DjangoGirls tutorial and put it in the `music` directory, or you can put it in the root directory of your app. Both ways are used
by developers. If you put your `templates` directory at the root level of the app, you need to update your `settings.py` file. 
A comparison of these two options can be found [here](https://learndjango.com/tutorials/template-structure). Django templates use
 special feature called the [Django Template Language](https://docs.djangoproject.com/en/4.1/ref/templates/language/) in order to inject
 bits of Python and data into a template. Django template language uses this syntax `{% %}` for Python and `{{ }}` for data.  
 
## Views

Django views are functions that process requests and generate responses. While we will see more options when we get to API's, for now
our views will be used to take a request that the user made to a URL and generate an `HttpResponse` that the user will see in the broswer.

## URLs

Django URLs are listed in the `urls.py` file and each path includes a pattern that the user will enter, a view, and a name. The `name` argument
is used as a shorthand by Django to refer to a path. An example of a path for a homepage looks like this.

```py
    path('/', views.index, name="home"),
```
