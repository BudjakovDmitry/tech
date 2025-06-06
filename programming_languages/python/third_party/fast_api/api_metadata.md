# Metadata and Docs URLs

## Metadata for API

You can set the following fields that are used in the OpenAPI specification and the
automatic API docs UIs:

| Parameter          | Type   | Description                                                                                               |
|--------------------|--------|-----------------------------------------------------------------------------------------------------------|
| `title`            | `str`  | The title of the API.                                                                                     |
| `summary`          | `str`  | A short summary of the API. Available since OpenAPI 3.1.0, FastAPI 0.99.0.                                |
| `description`      | `str`  | A short description of the API. It can use Markdown.                                                      |
| `version`          | `str`  | The version of the API. This is the version of your own application, not of OpenAPI. For example `2.5.0`. |
| `terms_of_service` | `str`  | A URL to the Terms of Service for the API. If provided, this has to be a URL.                             |
| `contact`          | `dict` | The contact information for the exposed API. It can contain several fields<sup>*</sup>.                   |
| `license_info`     | `dict` | The license information for the exposed API. It can contain several fields<sup>**</sup>.                  |

\* Contact fields:

| Parameter | Type | Description                                                                                       |
|-----------|------|---------------------------------------------------------------------------------------------------|
| `name`    | `str` | The identifying name of the contact person/organization.                                         |
| `url`     | `str` | The URL pointing to the contact information. MUST be in the format of a URL.                     | 
| `email`   | `str` | The email address of the contact person/organization. MUST be in the format of an email address. |

\** License info fields

| Parameter    | Type  | Description                                                                                                                                         |
|--------------|-------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`       | `str` | REQUIRED (if a license_info is set). The license name used for the API.                                                                             |
| `identifier` | `str` | An SPDX license expression for the API. The identifier field is mutually exclusive of the url field. Available since OpenAPI 3.1.0, FastAPI 0.99.0. |
| `url`        | `str` | A URL to the license used for the API. MUST be in the format of a URL.                                                                              |

```python
from fastapi import FastAPI

description = """
ChimichangApp API helps you do awesome stuff. 🚀

## Items

You can **read items**.

## Users

You will be able to:

* **Create users** (_not implemented_).
* **Read users** (_not implemented_).
"""

app = FastAPI(
    title="ChimichangApp",
    description=description,
    summary="Deadpool's favorite app. Nuff said.",
    version="0.0.1",
    terms_of_service="http://example.com/terms/",
    contact={
        "name": "Deadpoolio the Amazing",
        "url": "http://x-force.example.com/contact/",
        "email": "dp@x-force.example.com",
    },
    license_info={
        "name": "Apache 2.0",
        "url": "https://www.apache.org/licenses/LICENSE-2.0.html",
    },
)


@app.get("/items/")
async def read_items():
    return [{"name": "Katana"}]
```

> You can write Markdown in the description field and it will be rendered in the output.