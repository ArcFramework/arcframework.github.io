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
