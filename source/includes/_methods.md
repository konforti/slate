# Persons
Persons objects allow you to track and manipulate user data. 

The API allows you to retrieve, and update your user (create & delete is on the way). 

You can retrieve individual user or the current user as well as a list of all your users.

## List all persons
> Definition

```md
GET http://example.com/api/v1/persons/
```

> Example Request

```shell
curl http://localhost:3000/api/v1/persons?limit=3 \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

> Example Response

```json
{
    "data": [
        {
            "_id": "54c0f152615af0970ae143a4",
            "email": "john@email.com",
            "mode": "on",
            "username": "john"
        },
        {
            "_id": "54c0f1b19a0a58095d12fb17",
            "email": "paul@email.com",
            "mode": "on",
            "username": "paul"
        }
    ],
    "pages": {
        "current": 1,
        "prev": 0,
        "hasPrev": false,
        "next": 0,
        "hasNext": false,
        "total": 1
    },
    "items": {
        "begin": 1,
        "end": 2,
        "total": 2
    },
    "filters": {
        "username": "",
        "limit": 20,
        "page": 1,
        "sort": "_id"
    }
}
```

Returns a list of your users. The users are returned sorted by creation date, 
with the most recently created users appearing first.

*Arguments:*

* <h3>username *optional*</h3><p>Filter by username. Default is none.</p>
* <h3>limit *optional*</h3><p>Limit the number of return items. Default is 20 items.</p>
* <h3>page *optional*</h3><p>The page number of the return items group. Default is 1</p>
* <h3>sort *optional*</h3><p>The field name to sort by. ASC 'fieldName' DESC '-fieldName'. Default is '-timeCreated'.</p>

## Retrieve a person

> Definition

```md
GET http://localhost:3000/api/v1/persons/:id/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/54c0f152615af0970ae143a4/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

> Example Response

```json
{
    "_id": "54c0f152615af0970ae143a4",
    "email": "john@email.com",
    "mode": "on",
    "resetPasswordExpires": "",
    "resetPasswordToken": "",
    "username": "john",
    "search": [
        "john",
        "john@email.com"
    ],
    "timeCreated": "2015-01-27T14:07:44.647Z",
    "verificationToken": "",
    "isVerified": "",
    "notes": [
        {
            "_id": "54c238dbb64d8f3253b566ef",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:04:43.523Z",
                "name": "admin"
            },
            "data": "Very important note"
        },
        {
            "_id": "54c238f6b64d8f3253b566f0",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:05:10.239Z",
                "name": "admin"
            },
            "data": "Don't forget"
        }
    ],
    "statusLog": [],
    "status": {
        "name": "Happy"
    },
    "roles": [
        {
            "_id": "editor",
            "name": "Editor"
        },
        {
            "_id": "writer",
            "name": "writer"
        }
    ]
}
```

Retrieves the details of an existing user. 
You need only supply the unique user identifier.

*Arguments:*

* <h3>id **required**</h3><p>The identifier of the user to be retrieved.</p>

## Retrieve current user

> Definition

```md
GET http://localhost:3000/api/v1/persons/current/:jwt/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/current/Tb5sXrRcsWziYaghhn6Ltyl2CGzLDZVK/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

> Example Response

```json
{
    "_id": "54c0f152615af0970ae143a4",
    "email": "john@email.com",
    "mode": "on",
    "resetPasswordExpires": "",
    "resetPasswordToken": "",
    "username": "john",
    "search": [
        "john",
        "john@email.com"
    ],
    "timeCreated": "2015-01-27T14:07:44.647Z",
    "verificationToken": "",
    "isVerified": "",
    "notes": [
        {
            "_id": "54c238dbb64d8f3253b566ef",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:04:43.523Z",
                "name": "admin"
            },
            "data": "Very important note"
        },
        {
            "_id": "54c238f6b64d8f3253b566f0",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:05:10.239Z",
                "name": "admin"
            },
            "data": "Don't forget"
        }
    ],
    "statusLog": [],
    "status": {
        "name": "Happy"
    },
    "roles": [
        {
            "_id": "editor",
            "name": "Editor"
        },
        {
            "_id": "writer",
            "name": "writer"
        }
    ]
}
```
Retrieves the details of current user. 
You need only supply the unique JWT (Json Web Token).
The JWT can be found in the cookie people.jwt

*Arguments:*

* <h3>jwt **required**</h3><p>The json web token of the user to be retrieve.</p>

## Update a person

> Definition

```md
PUT http://localhost:3000/api/v1/persons/:id/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/54c0f152615af0970ae143a4/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2: \
   -d mode="on"
```

> Example Response

```json
{
    "_id": "54c0f152615af0970ae143a4",
    "email": "john@email.com",
    "mode": "off",
    "resetPasswordExpires": "",
    "resetPasswordToken": "",
    "username": "john",
    "search": [
        "john",
        "john@email.com"
    ],
    "timeCreated": "2015-01-27T14:07:44.647Z",
    "verificationToken": "",
    "isVerified": "",
    "notes": [
        {
            "_id": "54c238dbb64d8f3253b566ef",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:04:43.523Z",
                "name": "admin"
            },
            "data": "Very important note"
        },
        {
            "_id": "54c238f6b64d8f3253b566f0",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:05:10.239Z",
                "name": "admin"
            },
            "data": "Don't forget"
        }
    ],
    "statusLog": [],
    "status": {
        "name": "Happy"
    },
    "roles": [
        {
            "_id": "editor",
            "name": "Editor"
        },
        {
            "_id": "writer",
            "name": "writer"
        }
    ]
}
```

Updates the specified user by setting the values of the parameters passed. 
Any parameters not provided will be left unchanged.

*Arguments:*

* <h3>username *optional*</h3><p>The user name of the user to be updated.</p>
* <h3>email *optional*</h3><p>The email to be updated.</p>
* <h3>mode *optional*</h3><p>The mode (on/off) to be updated.</p>
* <h3>FIELD *optional*</h3><p>The FIELD (custom field) to be updated.</p>

## Assign a role to a user

> Definition

```md
POST http://localhost:3000/api/v1/persons/:id/roles/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/54c0f152615af0970ae143a4/roles/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2: \
   -d role="editor"
```

> Example Response

```json
{
    "_id": "54c0f152615af0970ae143a4",
    "email": "john@email.com",
    "mode": "off",
    "resetPasswordExpires": "",
    "resetPasswordToken": "",
    "username": "john",
    "search": [
        "john",
        "john@email.com"
    ],
    "timeCreated": "2015-01-27T14:07:44.647Z",
    "verificationToken": "",
    "isVerified": "",
    "notes": [
        {
            "_id": "54c238dbb64d8f3253b566ef",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:04:43.523Z",
                "name": "admin"
            },
            "data": "Very important note"
        },
        {
            "_id": "54c238f6b64d8f3253b566f0",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:05:10.239Z",
                "name": "admin"
            },
            "data": "Don't forget"
        }
    ],
    "statusLog": [],
    "status": {
        "name": "Happy"
    },
    "roles": [
        {
            "_id": "editor",
            "name": "Editor"
        },
        {
            "_id": "writer",
            "name": "writer"
        }
    ]
}
```

Add a role to the specified user.

*Arguments:*

* <h3>role **required**</h3><p>The role name to be added.</p>

## Remove a role from a user

> Definition

```md
DELETE http://localhost:3000/api/v1/persons/:id/roles/:role/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/54c0f152615af0970ae143a4/roles/writer/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2: \
   -X DELETE
```

> Example Response

```json
{
    "_id": "54c0f152615af0970ae143a4",
    "email": "john@email.com",
    "mode": "off",
    "resetPasswordExpires": "",
    "resetPasswordToken": "",
    "username": "john",
    "search": [
        "john",
        "john@email.com"
    ],
    "timeCreated": "2015-01-27T14:07:44.647Z",
    "verificationToken": "",
    "isVerified": "",
    "notes": [
        {
            "_id": "54c238dbb64d8f3253b566ef",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:04:43.523Z",
                "name": "admin"
            },
            "data": "Very important note"
        },
        {
            "_id": "54c238f6b64d8f3253b566f0",
            "userCreated": {
                "id": "54c0f152615af0970ae143a4",
                "time": "2015-01-23T12:05:10.239Z",
                "name": "admin"
            },
            "data": "Don't forget"
        }
    ],
    "statusLog": [],
    "status": {
        "name": "Happy"
    },
    "roles": [
        {
            "_id": "editor",
            "name": "Editor"
        }
    ]
}
```

Remove a role from the specified user.

*Arguments:*

* <h3>role **required**</h3><p>The role name to be removed.</p>

# Roles

## List all roles

> Definition

```md
GET http://localhost:3000/api/v1/roles/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/roles/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

> Example Response

```json
{
    "data": [
        {
            "_id": "root",
            "name": "Root"
        },
        {
            "_id": "writer",
            "name": "writer"
        }
    ],
    "pages": {
        "current": 1,
        "prev": 0,
        "hasPrev": false,
        "next": 0,
        "hasNext": false,
        "total": 1
    },
    "items": {
        "begin": 1,
        "end": 2,
        "total": 2
    },
    "filters": {
        "name": "",
        "limit": 20,
        "page": 1,
        "sort": "_id"
    }
}
```

Returns a list of roles.

## Retrieve existing role

> Definition

```md
GET http://localhost:3000/api/v1/roles/:rid/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/roles/editor/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

> Example Response

```json
{
    "_id": "editor",
    "permissions": ["can edit post"],
    "name": "editor"
}
```
Retrieves the details of a role. 
You need only supply the unique role ID.

*Arguments:*

* <h3>role **required**</h3><p>The role ID of the role to be retrieved.</p>
