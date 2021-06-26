**Table of contents**
- [Laravel Package Starter Kits](#laravel-package-starter-kits)
  - [Directory Structure 🗂️](#directory-structure-️)
  - [Package Skeleton 🦴](#package-skeleton-)
  - [Development Environment 🌱](#development-environment-)
  - [การ import package ที่เรากำลังพัฒนาเข้าไปใน laravel project ซึ่งอยู่บนเครื่องของเราแบบ locally 🏠](#การ-import-package-ที่เรากำลังพัฒนาเข้าไปใน-laravel-project-ซึ่งอยู่บนเครื่องของเราแบบ-locally-)
  - [สิ่งที่ต้องปรับเปลี่ยนก่อนทำการ Coding ✅](#สิ่งที่ต้องปรับเปลี่ยนก่อนทำการ-coding-)
  - [License](#license)

# Laravel Package Starter Kits
 
ชุดตั้งต้นใช้สำหรับการเริ่มสร้าง Laravel Package

## Directory Structure 🗂️

```
- src
- tests
CHANGELOG.md
README.md
LICENSE
composer.json
```

## Package Skeleton 🦴

สำหรับการเริ่มต้นสร้าง package เราไม่จำเป็นที่จะต้องวาง package ของเราเอาไว้ใน laravel project folder ก็ได้

ผมแนะนำให้เราสร้าง folder package วางไว้ในระดับเดียวกันกับ folder ของ laravel project ที่เราจะเอาไว้ใช้ทดสอบ package ของเรา

ตัวอย่างเช่น ผมสร้าง package เอาไว้ที่ `~/packges/` โดยที่ตัว folder ของ laravel ผมก็วางเอาไว้ที่ระดับเดียวกันกับ package ก็ได้ `~/laravel-website`

## Development Environment 🌱

ให้เราปรับแก้ไฟล์ต่างๆ ที่มีอยู่ใน [Directory Structure](#directory_structure) ตามความต้องการได้เลย

## การ import package ที่เรากำลังพัฒนาเข้าไปใน laravel project ซึ่งอยู่บนเครื่องของเราแบบ locally 🏠

ตัวอย่างเช่น ในกรณีที่เราวาง package ที่เราสร้างไว้ในระดับเดียวกันกับ laravel project ที่เรากำลังพัฒนา

```
/packages/my-package
/laravel-website
```

เราสามารถเรียก package ที่อยู่บนเครื่อง local ของเราได้ตามตัวอย่างด้านล่างนี้ได้

```json  
// laravel-website/composer.json

{
  "scripts": { ... },

  "repositories": [
    {
      "type": "path",
      "url": "../packages/my-package"
    }
  ]
}
```

จากนั้นเราต้องทำการเรียกคำสั่ง composer require เพื่อเพิ่ม package ที่เรากำลังทำการพัฒนาให้เข้ามารวมอยู่ใน autoload ด้วยคำสั่งด้านล่างนี้ครับ 

> ชื่อของ pacakge ก็ตามที่เราตั้งเอาไว้ใน `composer.json` เลยครับ เช่นของผมตั้งไว้ว่า 
> 
```json
// /packages/my-package/composer.json

{
    "name": "uatthaphon/packagename"
    ...
},
```

ผมก็รันคำสั่งเรียกเป็น

```sh
comsopser require uatthaphon/packagename
```

## สิ่งที่ต้องปรับเปลี่ยนก่อนทำการ Coding ✅

- [ ] แก้ข้อมูลใน `LICENSE` ไฟล์

```md
// LICENSE

Copyright (c) Atthaphon Urairat <- เปลี่ยนตรงนี้ครับ
```

- [ ] แก้ข้อมูลใน `composer.json`

```
// pacakges/my-package/composer.json

{
    "name": "uatthaphon/package-name", <- เปลี่ยนตรงนี้ครับ
    
    ...

    "authors": [
        {
            "name": "Atthaphon Urairat", <- เปลี่ยนตรงนี้ครับ
            "email": "u.atthaphon@gmail.com" <- เปลี่ยนตรงนี้ครับ
        }
    ],
    
    ...
    "autoload": {
        "psr-4": {
            "Uatthaphon\\PackageName\\": "src" <- เปลี่ยนตรงนี้ครับ
        }
    },
    "autoload-dev": {
        "psr-4": {
            "Uatthaphon\\PackageName\\Tests\\": "tests" <- เปลี่ยนตรงนี้ครับ
        }
    },
    
    ...

    "extra": {
        "laravel": {
            "providers": [
                "Uatthaphon\\PackageName\\PackageNameServiceProvider" <- เปลี่ยนตรงนี้ครับ
            ]
        }
    },
}

```    

- [ ] แก้ชื่อไฟล์ตั้งต้น และ `namespace`

ชื่อของไฟล์ที่ต้องเปลี่ยน

```sh
src/PackageNameServiceProvider.php
```

namespace ที่ต้องเปลี่ยน

```php
// src/PackageNameServiceProvider.php

<?php

namespace Uatthaphon\PackageName; <- เปลี่ยนตรงนี้ครับ

```

> Happy Coding ครับ 🥰🥰🥰

อีกนิดครับ ใน `composer.json` มี script ที่เอาไว้รัน test แล้วครับ ดังนั้นเราไม่ต้องเพิ่มคำสั่งยาวๆอย่าง `./vendor/phpunit/phpunit/phpunit` เพื่อทำการเทสนะครับ ให้ใช้คำสั่งนี้ก็พอ

```sh
composer test

composer testUnit

composer testFeature

composer testVerbose

```
## License

The MIT License (MIT). Please see [License File](LICENSE) for more information.
