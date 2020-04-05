---
description: >-
  For each entity we create a file called settings.js to group basic properties
  of its domain
---

# Settings File

## `path`

This property will indicate which will be the base route that will be used in the routes that will be created to access the screens of this domain.

## `domain`

It is a string with the path from the `domains/` folder using[`kabeb-case`](https://en.toolpage.org/tool/kebabcase) for the folder names and period \(`.`\) As the level separator. For an entity in`src/domain/Sale/Order` we will have`sale.order`. For compound names like`Sale/OrderItem` we will have`sale.order-item`, replacing the capital letter in the middle with hyphen \(`-`\) followed by the same letter that was capitalized by its lowercase version.

## `resource`

The`resource`is the base endpoint of the entity in the`API RESTful` that will be consumed. It can be something like`/posts` or`blog/posts` and it will be the final part of the URL that will be used to compose the requests that will be made to manage the resources. If the API is mounted on top of `http://localhost:8000` \(in`.env` files this will be the value of the variable`VUE_APP_REST_BASE_URL`\) the final URL will be`http://localhost:8000/posts` or`http://localhost:8000/blog/posts`, according to the examples mentioned above. On top of this URL, the verbs`GET`, `POST`, `PUT`, `PATCH` and `DELETE` will be applied.

