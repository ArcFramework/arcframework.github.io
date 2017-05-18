# Models

Arc allows you to use Laravel's powerful Eloquent engine to access the database. To do this you can set up Model classes
which map to rows in the database. See [Laravel's Eloquent Documentation](https://laravel.com/docs/master/eloquent) for
more information about Eloquent models. 

In addition to this Arc includes some default Eloquent models out of the box which represent WordPress's built-in data.

## User

### `findByEmail($email)` (static)

This static method returns the User matching the given email address or null if none exists.

```php
$user = User::findByEmail('user@domain.com');
```

### `findByUsername($username)` (static)

This static method returns the User matching the given username (user_login) address or null if none exists.

```php
$user = User::findByUsername('monkeypants_02');
```

### `makeAdministrator()`

Sets the user's role to 'administrator'.

```php
$user->makeAdministrator();
```

### `setRole($role)`

Sets the user's role to the given role.

```php
$user->setRole('administrator');
```

### `setMeta($key, $value)`

Sets the given usermeta key to the given value if a key value pair is provided or sets the key value pairs in the array if
an array is provided as the first argument. The usermeta database record will be created if it does not already exist.

```php
// We can pass in a key and a value as the first and second parameters
$user->setMeta('billing_country', 'Australia');
```
```php
// Alternatively we could pass in an associative array to set multiple key value pairs at once
$user->setMeta([
    'billing_country' => 'Australia',
    'billing_city' => 'Sydney'
]);

### `findMeta($key, $single = true)`

Returns the usermeta value matching the given key. To return multiple values if they are avaiable pass false as the
second paramater, otherwise only the first will be returned

Sets the given usermeta key to the given value if a key value pair is provided or sets the key value pairs in the array if
an array is provided as the first argument. The usermeta database record will be created if it does not already exist.

```php
$user->findMeta('first_name');
```
