MFX provides fundational tools to implement user management.

However, as different websites and APIs have different needs, these tools are voluntarily designed to be as flexible as possible and let you control how your users sign up and log in.

## User Storage

By default, MFX users are stored in a table called `mfx_users`.

However, this parameter and others can be overriden thanks to specific [configuration directives](Configuration-Directives#user-management).

The `mfx_users` table has no requirement about its structure, except it must contain a `user_id` field that serves as the unique user identifier or key. Besides this field, you can add to the table any amount of additional data you like.

## User Sign Up

It is your responsability to handle the sign up procedure for your users. That includes providing a form to gather sign up information (email, name, phone number, whatever you need), handling the sign up request through a specific route, then creating the record in the database for the user.

Once a user is signed up, you must notify MFX to make them the current user. The following paragraph explains how to initiate a session.

## Initiating a User Session

In order to initiate a session for a user, either after sign up or log in, you need to call the `User::validateWithFields` method with the adequate parameters depending on your setup.

For the sake or our example, we will settle that:

- Our users log in with an email and a password
- The email is stored in the `user_email` field
- The password is stored in the `user_password` field and hashed using the `SHA1` algorithm

Our example also uses the [[Data Validator]] to validate the input data.

```php
#[Route, AnonymousRoute]
public static function signIn() {
    $validator = new DataValidator();
    $validator->createField('email', FieldType::EMAIL);
    $validator->createField('password', FieldType::TEXT);

    // Checking POST input
    if ($validator->validate($_POST)) {
        $fields = [
            [ 'name' => 'user_email', 'value' => $validator['email'] ],
            [ 'name' => 'user_password', 'value' => $validator['password'], 'function' => 'SHA1' ]
        ];
        if (!User::validateWithFields($fields)) {
            trigger_error(_('Invalid user name and/or password.'));
        }
    }

    return RequestResult::buildRedirectRequestResult();
}
```

If the `User::validateWithFields` method returns `true`, the session is then valid for this user. Any subsequent call to a MFX route will have this user logged in until either the session is lost, or the user actively logs out.

## Ending a Session

You can very easily end a session for the current user by calling the `User::invalidate()` method.

## Accessing User Data

When an active session exists, you can retrieve any additional user data that is part of the `mfx_users` table thanks to the current user's instance.

Let's say you have a user's address stored in a `user_address` field in the `mfx_users` table. You can get this information back like this:

```php
$address = User::currentUser()->user_address;
```

However, if you need to access custom data outside of the `mfx_users` table or apply some transformation to this data, you may need to subclass the `User` class as described below.

## Handling Custom Data Structures

The default `User` class handles most data available in the `mfx_users` table. However, in many cases, you may need to access custom data stored in other tables or even other servers.

In order to do that, you need to subclass the `User` class. You can instruct MFX to use your custom class thanks to the [`user_management.class` configuration directive](Configuration-Directives#user-management).

All you need to do in your custom subclass is to override the `fetchData()` method. In its defaults implementation, this method returns the data row from `mfx_users` for the active user. Your custom implementation must continue to return this row, but you can add as many information you need to it. Or even transform some data if needed.

> [!NOTE]
> Other methods, like `fetchDataQuery()`, can be overridden if needed, or in place of the `fetchData()` method. Please take a look at the [source code of the `User` class](https://github.com/chsxf/mfx/blob/main/src/chsxf/MFX/User.php) for more information.

For example:

```php
class CustomUser extends User {

    protected function fetchData(): mixed {
        $row = parent::fetchData();
        if ($row === false) {
            return false;
        }

        $items = $this->fetchPurchasedItems();
        if ($items === false) {
            return false;
        }
        $row['items'] = $items;
        return $row;
    }

    protected function fetchPurchasedItems() {
        $sql = "SELECT `item_name` FROM `purchased_items` WHERE `user_id` = ?";
        $dbm = DatabaseManager::open();
        return $dbm->getColumn($sql, $this->getKey());
    }

}
```

You can them access the purchased items list by calling `User::currentUser()->items`.
