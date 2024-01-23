# REST API Development 101

---

## REST is a convention for structuring API data

REST (shorthand for “Representational State Transfer”) is a set of guidelines for how to represent information in an API that provides data by means of HTTP requests. 

---

## Data in your API is represented as resources

Resources are usually the **nouns** in your project -- the things you are representing in your application.

- shopping lists
- shopping list items
- notes
- albums
- songs

---

### RESTful APIs provide endpoints to access data

You can think of an endpoint as an HTTP Method + URL + resource

`GET /shopping-lists`

**returns a JSON array of all shopping lists**

---

## Methods map to CRUD actions

| HTTP method | CRUD action      | SQL    |
| ----------- | ---------------- | ------ |
| POST        | Create           | INSERT |
| GET         | Read (Retrieve)  | SELECT |
| PUT         | Update (replace) | UPDATE |
| PATCH       | Update (partial) | UPDATE |
| DELETE      | Destroy          | DELETE |

---

## Different HTTP methods for the same path

| HTTP method | URL             | resource / action          |
| ----------- | --------------- | -------------------------- |
| GET         | /shopping-lists | list of all shopping lists |
| POST        | /shopping-lists | create a new shopping list |

---

## Resources can be **single** or a **collection**

**collection**
```
GET /shopping-lists/
```

**single**

```
GET /shopping-lists/1
```

#### An id identifies a single resource. In this example, the id is `1`.

---

## Different HTTP methods for the same path

### for a single resource

| HTTP method | URL       | resource      |
| ----------- | --------- | ---------------------------- |
| GET         | /shopping-lists/1 | one shopping list with id 1          |
| PUT/PATCH   | /shopping-lists/1 | update shopping list with id 1       |
| DELETE      | /shopping-lists/1 | delete shopping list with id 1       |

---

## Resources can be **nested to show relationships**

Related resources can be **nested.** This can show a relationship between two resources by nesting the URL for one resource inside the URL for another resource.

`GET /lists/1/items`

The above URL combines a **single** resource with a **collection** resource.

---

## Resources can be **filtered** with **query parameters**

For example, you may want to show all the items on a shopping list that are in the “produce” category.

```
GET /lists/1/items?category=produce
```

---

## **Best Practices for your REST API**

---

### 📌 Use lower-case letters in the URL

✅ `/items`

❌ `/Items`

---

### 📌 Use hyphens (kebab-case) instead of underscores or camelCase in the URL

✅ `/shopping-lists`

❌ `/shoppingLists`

❌ `/shopping_lists`

---

### 📌 Don’t use CRUD verbs in the URL

#### the HTTP method already has a verb that maps to a CRUD action

✅ PATCH `shopping-lists/1`

❌ PATCH `shopping-lists/1/edit`

---

### 📌 Use plural nouns for consistency

✅ `/shopping-lists/1`

❌ `/shopping-list/1`

---

### 📌 Use nouns instead of verbs

✅ `/shopping-lists/1/items`

❌ `/shopping-lists/1/get-items`

---

### 📌 Use clear names for resources, not abbreviations

✅ `/shopping-lists/1/items`

❌ `/sl/1/i`

---

### 📌 Don’t nest resources unnecessarily

Nesting is helpful if you need to use some information in the URL path (like an id) to look things up in the database, but try to avoid nesting more than one level deep.

❌ `shopping-lists/1/items/4`

✅ `items/4`

---

### 📌 Consider what you should include in your API and what you should leave out

For example, you probably don’t want to provide a list of all your application’s users, except to users with special permissions.

---

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

---

### 📌 Return error codes

If a user makes a request that your API can’t handle, return an error message that explains what went wrong.

```js
res.status(404).json({ message: "Shopping list not found" });
```

---

Status codes are better with cats.

![fit](https://http.cat/401)

--- 

Or dogs

![fit](https://httpstatusdogs.com/img/200.jpg)

---

### 📌 Use pagination

Paginating your API lets you manage large amounts of data, preventing your responses from becoming too slow and unwieldy.

```
GET /shopping-lists?page=1&limit=50
```

For example, if a request would return 500 objects, your response may return the first set of 50 records with a link to the next set of 50 (and so on). The client would make another request to get the next set of 50 records.

---

### 📌 Document your API

So that your users know what your endpoints are, how to use them, and what to expect in response. 

There are tools that you can use to generate documentation, but you can also just write up your endpoints and how they work in a README.md file in your repo.

---

### 📌 Use versioning

Versioning your API lets you make changes to your API without breaking existing clients.

```
GET https://shopping-list-api.com/v1/shopping-lists
```

---

# These are guidelines for humans

### So do what you think is best for your use case

There are no enforceable rules for REST APIs.

The most important thing is to be consistent and to make sure that your API is easy to use and understand.
