# Generic views

Typically, when using the generic views, you'll override the view, and set several class
attributes.

## GenericAPIView

This class extends REST framework's `APIView` class, adding commonly required behavior
for standard list and detail views.

Each of the concrete generic views provided is built by combining `GenericAPIView`, with
one or more mixin classes.

### Attributes

The following attributes control the basic view behaviour.

- `queryset` - the queryset that should be used for returning objects from this view.
Typically, you must either set this attribute, or override the `get_queryset()` method.
If you are overriding a view method, it is important that you call `get_queryset()`
instead of accessing this property directly, as `queryset` will get evaluated once, and
those results will be cached for all subsequent requests.
- `serializer_class` - the serializer class that should be used for validating and
deserializing input, and for serializing output. Typically, you must either set this
attribute, or override the `get_serializer_class()` method.
- `lookup_field` - the model field that should be used for performing object lookup of
individual model instances. Defaults to `'pk'`. Note that when using hyperlinked APIs
you'll need to ensure that both the API views and the serializer classes set the lookup
fields if you need to use a custom value.
- `lookup_url_kwarg` - the URL keyword argument that should be used for object lookup.
The URL conf should include a keyword argument corresponding to this value. If unset
this defaults to using the same value as `lookup_field`.

The following attributes are used to control pagination when used with list views.

- `pagination_class` - the pagination class that should be used when paginating list
results. Defaults to the same value as the `DEFAULT_PAGINATION_CLASS` setting, which is
`'rest_framework.pagination.PageNumberPagination'`. Setting `pagination_class=None` will
disable pagination on this view.

Filtering:

- `filter_backends` - a list of filter backend classes that should be used for filtering
the queryset. Defaults to the same value as the `DEFAULT_FILTER_BACKENDS` setting.
