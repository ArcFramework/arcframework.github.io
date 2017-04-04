[Home](index.md) / Controllers

# Controllers

Controllers should extend the `Arc\Http\Controllers\BaseController` class. This will give them access to the following
methods:

1. [abort()](#abort)
1. [makeValidator()](#make-validator)
1. [redirect()](#redirect)
1. [response()](#response)

## `abort()`

The abort method throws a HTTP exception which will be rendered by the exception handler:

```php?start_inline=1
$this->abort(401);
```

You may also provide the exception's response text:
    
```php
    $this->abort(401, 'Unauthorized.');
```

## `makeValidator($requestParameters, $rules)`

Pass in an array of request parameters and an array of rules to generate an instance of Laravel's
`Illuminate\Validation\Validator` class. Calling this method is analogous to calling `make()` on Laravel's `Validator` facade.

## `redirect()`

The redirect method returns a redirect HTTP response, or returns the redirector instance if called with no arguments:

```php
return $this->redirect('/home');

return $this->redirect()->route('route.name');
```

```php
return $this->response('Hello World', 200, $headers);

return $this->response()->json(['foo' => 'bar'], 200, $headers);
```

## `response()`

The response method creates a response instance or obtains an instance of the response factory:

```php
return $this->response('Hello World', 200, $headers);

return $this->response()->json(['foo' => 'bar'], 200, $headers);
```
