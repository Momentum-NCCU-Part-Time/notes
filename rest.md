# REST API Development 101

## HTTP Methods, CRUD, & Database actions

| HTTP method | CRUD action     | SQL                                 |
| ----------- | --------------- | ----------------------------------- |
| POST        | Create          | INSERT                              |
| GET         | Read (Retrieve) | SELECT                              |
| PUT/PATCH   | Update          | UPDATE                              |
| DELETE      | Destroy         | DELETE                              |

## REST is a convention for structuring API data

REST (shorthand for “Representational State Transfer”) is a set of guidelines for how to represent information in an API that provides data by means of HTTP requests. We consider this data “resources.” Resources in your API are usually the *nouns* in your project -- the things you are representing in your application.

### RESTful APIs provide endpoints to access data

You can think of an endpoint as an HTTP Method + URL + resource

## Resources can be single or a collection

Resources can be **single** or a **collection**. Shopping lists are a resource in shopping list project; so are items on a shopping list. Some resources you need for the shopping list project are::

- *details about one specific shopping list* (a **single** resource)
- *a list of all your shopping lists* (a **collection** resource)
- *a list of all your items on a shopping list* (a **collection** resource)`

Almost all REST APIs implement urls like the following to provide CRUD actions for single and collection resources.

| HTTP method | URL       | Description of resource      |
| ----------- | --------- | ---------------------------- |
| GET         | /shopping-lists   | list of all shopping lists           |
| POST        | /shopping-lists   | create a new shopping list |
| GET         | /shopping-lists/1 | one shopping list with id 1          |
| PUT/PATCH   | /shopping-lists/1 | update shopping list with id 1       |
| DELETE      | /shopping-lists/1 | delete shopping list with id 1       |

## Resources can be **nested to show relationships**

Related resources can be **nested.** This means that you can show the relationship between two resources by nesting the URL for one resource inside the URL for another resource.

For example, you may want to show shopping list items related to a single shopping list.

You could represent all the items (collection) for a specific shopping list like so:

| GET | /lists/1/items | Show all items for shopping list with id 1|
| --- | ----------------------- | ------------------------------------------ |

## **Best Practices for your REST API**

### 📌 Use lower-case letters in the URL

✅ `/items`

❌ `/Items`

### 📌 Use hyphens (kebab-case) instead of underscores or camel-case in the URL

✅ `/shopping-lists`

❌ `/shoppingLists`

❌ `/shopping_lists`

### 📌 Don’t use CRUD verbs in the URL; the HTTP method already has a verb that maps to a CRUD action

✅ PATCH `shopping-lists/1`

❌ PATCH `shopping-lists/1/edit`

### 📌 Don’t nest resources unless you need to use some information in the URL path (like an id) to look things up in the database in your view

❌ `shopping-lists/1/items/4`

✅ `items/4`

### 📌 Consider what you should include in your API and what you should leave out

For example, you probably don’t want to provide a list of all your application’s users, except to users with special permissions.

### 📌 Use the right [status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

Some of the most common status codes are:

| Status Code | Description                                                  |
| ----------- | ------------------------------------------------------------ |
| 200         | OK                                                           |
| 201         | Created                                                      |
| 204         | No Content                                                   |
| 400         | Bad Request                                                  |
| 401         | Unauthorized                                                 |
| 403         | Forbidden                                                    |
| 404         | Not Found                                                    |
| 405         | Method Not Allowed                                           |

### 📌 Use [pagination](https://www.django-rest-framework.org/api-guide/pagination/#pagination)

Paginating your API lets you manage large amounts of data, preventing your responses from becoming too slow and unwieldy.

For example, if a request would return 200 objects, your response may return the first set of 50 records with a link to the next set of 50 (and so on).

### 📌 Document your API

So that your users know what your endpoints are, how to use them, and what to expect in response. There are tools that you can use to generate documentation, but you can also just write up your endpoints and how they work in a README.md file in your repo.
