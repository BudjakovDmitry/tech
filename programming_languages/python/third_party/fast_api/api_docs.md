# Interactive API docs

Fast API provides automatic interactive API documentation provided by Swagger UI. You
can see it by visiting

```
/docs
```

Alternatively you can see the automatic documentation provided by ReDoc. You can see it
visiting

```
/redoc
```

## OpenAPI

FastAPI generates a "schema" with all your API using the OpenAPI standard for defining
APIs.

A __schema__ is a definition or description of something.

An __API schema__ includes your API paths, the possible parameters they take, etc.

A __data schema__ includes the JSON attributes and data types they have, etc.

OpenAPI defines an API schema for your API. And that schema includes definitions (or
"schemas") of the data sent and received by your API using JSON Schema, the standard for
JSON data schemas.

FastAPI automatically generates a JSON (schema) with the descriptions of all your API.
You can see it directly at: http://127.0.0.1:8000/openapi.json

The OpenAPI schema is what powers the two interactive documentation systems included.
And there are dozens of alternatives, all based on OpenAPI. You could easily add any of
those alternatives to your application built with FastAPI.

You could also use it to generate code automatically, for clients that communicate with
your API. For example, frontend, mobile or IoT applications.
