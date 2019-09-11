---
title: php数组的一些应用
date: 2019-09-11 21:22:29
tags: php数组
category: php
---


php 数组很好很强大，下面展示一些个人常用到的事例

```php
$example = [
    0 => [
        'id' => 1,
        'name' => 'alpha',
        'age' => 18,
    ],
    1 => [
        'id' => 22,
        'name' => 'berry',
        'age' => 28,
    ],
    2 => [
        'id' => 33,
        'name' => 'cherry',
        'age' => 38,
    ]
];
```

### 返回二维数组指定的列的集合

`array_column($example, 'id')`

```php
Array
(
    [0] => 1
    [1] => 22
    [2] => 33
)
```

### 传递指定的两个字段，并按照指定的字段组成新的一维数组

`array_column($example, 'name', 'id');`

```php
Array
(
    [1] => alpha
    [22] => berry
    [33] => cherry
)
```

### 二维数组，指定值作为key

`array_column($example, null, 'id')`
```php
Array
(
    [1] => Array
        (
            [id] => 1
            [name] => alpha
            [age] => 18
        )

    [22] => Array
        (
            [id] => 22
            [name] => berry
            [age] => 28
        )

    [33] => Array
        (
            [id] => 33
            [name] => cherry
            [age] => 38
        )

)
```

### 获取二维数组指定key的汇总

```php
$sum = array_sum(array_map(function($val) {
    return $val['age'];
}, $example));
echo $sum; \\ 84
```

