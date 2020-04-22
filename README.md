<p align="center">
    <a href="https://codeigniter.com/" target="_blank">
        <img src="https://codeigniter.com/assets/images/ci-logo-big.png" height="100px">
    </a>
    <h1 align="center">CodeIgniter PHPUnit Test</h1>
    <br>
</p>

CodeIgniter 3 PHPUnit Test extension library

[![Latest Stable Version](https://poser.pugx.org/nueip/codeigniter-phpunit/v/stable?format=flat-square)](https://packagist.org/packages/nueip/codeigniter-phpunit)
[![License](https://poser.pugx.org/nueip/codeigniter-phpunit/license?format=flat-square)](https://packagist.org/packages/nueip/codeigniter-phpunit)

This RESTful API extension is collected into [nueip/codeigniter-pack](https://github.com/nueip/codeigniter-pack) which is a complete solution for Codeigniter framework.

FEATURES
--------

- ***PHPUnit Test** in **Codeigniter 3** Framework*

- *Easy to install into your Codeigniter project by Composer*

---

OUTLINE
-------

- [FEATURES](#features)
- [OUTLINE](#outline)
- [REQUIREMENTS](#requirements)
- [INSTALLATION](#installation)
- [DIRECTORY STRUCTURE](#directory-structure)
- [CONFIGURATION](#configuration)
- [USAGE](#usage)
- [TEST CASE](#test-case)


REQUIREMENTS
------------

This library requires the following:

- PHP 5.3.0+
- CodeIgniter 3.0.0+

---

INSTALLATION
------------

Run Composer in your Codeigniter project under the folder `\application`:

    composer require nueip/codeigniter-phpunit

---

DIRECTORY STRUCTURE
-------------------

```
codeigniter/
└── application/
    ├── tests/          Test cases
    ├── vendor/         Vendor included nueip/codeigniter-phpunit
    └── phpunit.xml     PHPUnit XML
```

---

CONFIGURATION
-------------

According to [Directory Structure](#directory-structure), create and configure `phpunit.xml` under `application` directory:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<phpunit bootstrap="vendor/nueip/codeigniter-phpunit/bootstrap.php">
  <testsuites>
    <testsuite name="TestSuite">
      <directory>tests</directory>
    </testsuite>
  </testsuites>
</phpunit>
```

For this `phpunit.xml` template, the test cases directory is `application/test`, make sure you would create every test cases under it.

---

USAGE
-----

In the `application` directory of this library, run `phpunit` from vendor:

```
$ ./vendor/bin/phpunit
```

Or using absolute path commands like:

```
$ /var/www/html/codeigniter3/application/vendor/bin/phpunit -c /var/www/html/codeigniter3/application/phpunit.xml
$ phpunit -c /var/www/html/codeigniter3/application/phpunit.xml
```

Then the result would like:

```ps
PHPUnit 5.7.27 by Sebastian Bergmann and contributors.



Time: 40 ms, Memory: 2.75MB

No tests executed!
```

---

TEST CASE
---------

With this extension libaray, you could write test cases with loading Codeigniter framework.

For example, write a test case `application/tests/CodeigniterTest.php` for testing Codeigniter config component:

```php
<?php

use PHPUnit\Framework\TestCase;

final class CodeigniterTest extends TestCase
{
    function __construct() 
    {
        parent::__construct();
        // Load CI application
        $this->CI = & get_instance();
    }
    
    public function testConfigItem()
    {
        $indexPage = $this->CI->config->item('index_page');
        
        $this->assertSame('index.php', $indexPage);
    }
}
```

Then you would get the result `OK (1 test, 1 assertion)` by running PHPUnit test.
