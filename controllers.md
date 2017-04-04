[Home](index.md) / Controllers

# Controllers

## Helper Methods

Global helper functions can be problematic in the WordPress plugin context, so we've implemented some of the useful global 
helper functions which you might be used to using in Laravel controllers as methods on the parent Controller class.

1. [abort()](#abort)
1. [response()](#response)

### `abort()`

The abort method throws a HTTP exception which will be rendered by the exception handler:

```php
$this->abort(401);
```

You may also provide the exception's response text:
    
```php
$this->abort(401, 'Unauthorized.');
```

### `response()`

The response method creates a response instance or obtains an instance of the response factory:

```php
return $this->response('Hello World', 200, $headers);

return $this->response()->json(['foo' => 'bar'], 200, $headers);
```
