## Grid Helper

To Modify the display output of column
```php
$grid->director()->display(function($userId) {
    return User::find($userId)->name;
});
--
or
--
$grid->text()->display(function($text) {
    return str_limit($text, 30, '...');
    or run any query and return ta value
});
--
or
--
$grid->column('column_name')->display(function($text) {
    return str_limit($text, 30, '...');
    or run any query and return ta value
});
```

If you want to run some group by query then you can do the following
```php
$gridquery = $grid->model()->groupBy('column_name', 'another_column_name')->select('column_name', 'another_column_name', DB::raw('SUM(some_value) as total'));
--
or
--
$gridquery = $grid->model()->groupBy('column_name', 'another_column_name')->select('column_name', 'another_column_name', DB::raw('count(some_value) as count'));
```

If you want to access the data of the grid in callback function you can follow this
```php
$grid->column('quantity', 'Quantity')->display(function () {
    $column = $this->column;
});
```
