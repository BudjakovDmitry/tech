# TokenAuthentication

> Note that token authentication provided by Django REST framework is a fairly simple
> implementation.
> 
> For an implementation which allows more than one token per user, has some tighter
> security implementation details, and supports token expiry, see [Django REST knox](
> https://github.com/jazzband/django-rest-knox) third party package.

This authentication scheme uses a simple token-based HTTP Authentication scheme. Token
authentication is appropriate for client-server setups, such as native desktop and
mobile clients.

To use the `TokenAuthentication` scheme you'll need to [configure the authentication
classes](README.md#setting-the-authentication-scheme) to include `TokenAuthentication`,
and additionally include `rest_framework.authtoken` in your `INSTALLED_APPS` setting.

```python
INSTALLED_APPS = [
    ...,
    'rest_framework.authtoken'
]
```

Make sure you run `manage.py migrate` after changing your settings. The
`rest_framework.authtoken` app provides Django database migrations.

You'll also need to create tokens for your users.

```python
from rest_framework.authtoken.models import Token

token = Token.objects.create(user=...)
print(token.key)
```

For clients to authenticate, the token key should be included in the `Authorization`
HTTP header. The key should be prefixed by the string literal "Token", with whitespace
separating the two strings.

```http request
Authorization: Token 9944b09199c62bcf9418ad846dd0e4bbdfc6ee4b
```

If you want to use different keyword in the header, such as `Bearer`, simply subclass
`TokenAuthentication` and set the `keyword` class variable.

If successfully authenticated, `TokenAuthentication` provides the following credentials:

- `request.user` will be a Django `User` instance;
- `request.auth` will be a `rest_framework.authtoken.models.Token` instance.

Unauthenticated responses that are denied permissions will result in an
`HTTP 401 Unauthorized` response with an appropriate WWW-Authenticate header.

```http request
WWW-Authenticate: Token
```

The `curl` command line tool may be useful for testing token authenticated APIs.

```shell
curl -X GET http://127.0.0.1:8000/api/example/ -H 'Authorization: Token 9944b09199c62bcf9418ad846dd0e4bbdfc6ee4b'
```

> **Note**: if you use `TokenAuthentication` in production you must ensure that your API
> is only available over *https*.
