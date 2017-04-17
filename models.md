# Models

Arc includes some default Eloquent models out of the box which represent WordPress's built-in data.

## User

### `findByEmail($email)`

Returns the User matching the given email address or null if none exists.

```php
$user = User::findByEmail('user@domain.com');
```

