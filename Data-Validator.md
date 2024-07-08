The Data Validator is one of, if not "the", most useful feature of MFX.

It serves two purposes: validating data structures (hence its name), and generating form fields based on the specified validation criteria.

You can validate anything you want as long as it is either an Array or an object implementing [`\Traversable`](https://www.php.net/manual/en/class.traversable.php). A very common use case is obviously validating request input data.

## Usage

You can create as many DataValidator instances as you want. You have to provide each instance with the list of fields you want to validate in a specific data structure. You do not need to list every field in the data structure, but only those you want to test against.

[Fields](Data-Validator-Fields) exist for a variety of data types.

Here is a simple example of data validation:

```php
$data = [
    'name' => 'John Doe',
    'email' => 'johndoe@example.com',
    'age' => '42'
];

// ...

$validator = new DataValidator();
$validator->createField('name', FieldType::TEXT);
$validator->createField('email', FieldType::EMAIL);
$validator->createField('age', FieldType::POSITIVE_INTEGER);

if ($validator->validate($data)) {
    // Data is valid - Proceed
}
else {
    // Data is invalid - Raise an error
}
```

## Data Filtering

In the previous example, the `age` field is validated as a strictly positive integer. But, in many cases, you may want to apply additional constraints on your data. Enter the [filters](Data-Validator-Filters).

Here's how to modify the previous example to add an age constraint of 13 or more:

```php
$ageField = $validator->createField('age', FieldType::POSITIVE_INTEGER);
$ageField->addFilter(new InIntRange(13, getrandmax()));
```

## Retrieving Validated Data

Once data has been successfully validated, you can safely retrieve it from the DataValidator instance itself. It ensures you that the data you will use further on is sanitized and conforms to your validation criteria.

**However, it does not prevent you from escaping data in your SQL queries for example.**

As the DataValidator conforms to [`\ArrayAccess`](https://www.php.net/manual/en/class.arrayaccess.php), you can easily access values as follow:

```php
if ($validator->validate($data)) {
    printf("Valid User Data for %s (%s, age: %d)", $validator['name'], $validator['email'], $validator['age']);
}
```

You can also use the various methods from the DataValidator such as `getFieldValue` or `getFieldValues` to retrieve data with more control.

## Using Data in Views

The data validator has been designed with templating in mind. Thus, you can safely pass it to the Twig template engine to be accessed by your view templates.

For example, your route can return it directly:

```php
return new RequestResult(NULL, [ 'validator' => $validator ]);
```

And you can use it in your Twig files as any other variable:

```twig
<p>Name of the User: {{ validator.name }}</p>
```

## Generating Form Fields

Finally, you can also use the data validator to generate HTML form fields directly for you. MFX includes a Twig extension dedicated to templating.

By using the following template, you will generate an HTML form:

```twig
<form>
    <div>
        <div>Name</div>
        <div>{% dv_field validator 'name' %}</div>
    </div>
    <div>
        <div>Email</div>
        <div>{% dv_field validator 'email' %}</div>
    </div>
    <div>
        <div>Age</div>
        <div>{% dv_field validator 'age' %}</div>
    </div>
    <div><button type="submit">Submit</button></div>
</form>
```

This will generate the following HTML code:

```html
<form>
  <div>
    <div>Name</div>
    <div><input type="text" name="name" id="name" /></div>
  </div>
  <div>
    <div>Email</div>
    <div><input type="email" name="email" id="email" /></div>
  </div>
  <div>
    <div>Age</div>
    <div><input type="number" name="age" id="age" min="1" /></div>
  </div>
  <div><button type="submit">Submit</button></div>
</form>
```
