---
title: 使用PHPCompatibility+PHP_CodeSniffer进行PHP版本的兼容性检查
date: 2020-12-18 23:09:30
tags: php
category: php
---

1. 编写composer.json 
```
{
    "require-dev": {
        "squizlabs/php_codesniffer": "3.*",
        "phpcompatibility/php-compatibility": "*"
    },
    "prefer-stable" : true,
    "scripts": {
        "post-install-cmd": "\"vendor/bin/phpcs\" --config-set installed_paths vendor/phpcompatibility/php-compatibility",
        "post-update-cmd" : "\"vendor/bin/phpcs\" --config-set installed_paths vendor/phpcompatibility/php-compatibility"
    }
}
```

2. composer update
3. ./vendor/bin/phpcs --standard=PHPCompatibility --runtime-set testVersion PHP版本 path --extensions=php --report=summary --report-file=/path