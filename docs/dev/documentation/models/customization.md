---
title: "Custom Models"
description: "Create your own Models"
---

Your own model class is ready after the following three steps:
## 1. Create a DCA

```php
// src/App/Resources/contao/dca/tl_example.php
$GLOBALS['TL_DCA']['tl_example'] = [
    ...
];
```

## 2. Create the Model class
The naming convention for the model class is to omit `tl_`, convert the snake_case to PascalCase and add "Model".

```php
// src/App/Model/ExampleModel.php
<?php

namespace App\Model;

use Contao\Model;

class ExampleModel extends Model
{
    protected static $strTable = 'tl_example';

    // if you have logic you need more often, you can implement it here
    public function setHash()
    {
        $this->hash = md5($this->id);
    }
}
```

## 3. Register the Model
```php
// src/App/Resources/contao/config/config.php

use App\Model\ExampleModel;

$GLOBALS['TL_MODELS']['tl_example'] = ExampleModel::class;
```

Now you're done and can use your own Model class! :-)