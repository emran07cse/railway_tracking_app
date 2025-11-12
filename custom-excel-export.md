#### To create a custom xlxs file export follow the following steps
Steps,
1. Create an exporter class under app/Admin/Exporters directory 
   
for example  
```php
<?php

Namespace App\Admin\Exporters;

use App\Admin\Models\SubCategory;
Use Encore\Admin\Grid\Exporters\ExcelExporter;
use Maatwebsite\Excel\Concerns\WithMapping;

class SubCategoryExporter extends ExcelExporter implements WithMapping{
    
    protected $fileName = 'your_preferred_name.xlsx';

    public function map($row) : array
    {
        return [
            $row->id,
            data_get($row, 'category.name'), //For Relational table data
            $row->sub_category_name,
            $row->description,
            $row->created_at,
            $row->updated_at,
        ];
    }

    public function headings(): array
    {
        return [
            '#',
            'Category Name',
            'Subcategory Name',
            'Description',
            'Created',
            'Updated'
        ];
    }
}
```

Add the following line in your controller
```php
use App\Admin\Exporters\SubCategoryExporter;
...


$grid->exporter(new SubCategoryExporter());
```
