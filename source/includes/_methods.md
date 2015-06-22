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
curl http://localhost:3000/api/v1/persons/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2:
```

> Example Response

```json
{
    "data": [
        {
            "_id": "54c0f152615af0970ae143a4",
            "email": "john@email.com",
            "isActive": "yes",
            "username": "john"
        },
        {
            "_id": "54c0f1b19a0a58095d12fb17",
            "email": "paul@email.com",
            "isActive": "yes",
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

Returns a list of your users. The users are returned sorted by creation date, with the most recently created customers appearing first.

Arguments:

* <h3>username</h3><p>Filter by username. Default is none.</p>
* <h3>limit</h3><p>Limit the number of return items. Default is 20 items.</p>
* <h3>page</h3><p>The page number of the return items group. Default is 1</p>
* <h3>sort</h3><p>The field name to sort by. ASC 'fieldName' DESC '-fieldName'. Default is '-timeCreated'.</p>

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
    "isActive": "yes",
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

## Retrieve current user

> Definition

```md
GET http://localhost:3000/api/v1/persons/current/:sid/
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
    "isActive": "yes",
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

sid = session ID name: peoplesid from cookies.
Be sure to encode the sid value in the request.

## Update a person

> Definition

```md
PUT http://localhost:3000/api/v1/persons/:id/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/54c0f152615af0970ae143a4/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2: \
   -d isActive="no"
```

> Example Response

```json
{
    "_id": "54c0f152615af0970ae143a4",
    "email": "john@email.com",
    "isActive": "no",
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

## Update a person fields

> Definition

```md
PUT http://localhost:3000/api/v1/persons/:id/fields/
```

> Example Request

```shell
$ curl http://localhost:3000/api/v1/persons/54c0f152615af0970ae143a4/fields/ \
   -u sk_A6D8FC87413B789E4E9E86FAC43A2: \
   -d lastName="lennon"
```

> Example Response

```json
{
    "record": {
        "_id": "54c0f152615af0970ae143a4",
        "email": "john@email.com",
        "isActive": "no",
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
    },
    "fields": [
        {
            "key": "firstName",
            "name": "First Name",
            "value": "John"
        },
        {
            "key": "lastName",
            "name": "Last Name",
            "value": "Lennon"
        }
    ]
}
```
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
    "isActive": "no",
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
    "isActive": "no",
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

