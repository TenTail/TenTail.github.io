---
title: Composer 記憶體不足
date: 2020-10-09 21:17:02
uri: composer-allowed-memory-size-exhausted
categories:
- Composer
tags:
- Composer
---

使用 `composer require` 或 `composer update` 時會經常遇到記憶體的問題。

```shell
PHP Fatal error:  Allowed memory size of 1610612736 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/Cellar/composer/1.10.7/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52

Fatal error: Allowed memory size of 1610612736 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/Cellar/composer/1.10.7/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

目前最簡單的解決方法是執行 composer 時不設定記憶體上限：

```shell
php -d memory_limit=-1 /usr/local/bin/composer
```
