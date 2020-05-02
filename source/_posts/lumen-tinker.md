---
title: Lumen 安裝 laravel/tinker
date: 2020-05-02 21:17:02
uri: lumen-tinker
categories:
- Laravel
tags:
- Laravel
- Lumen
---

> 本文章使用的 Lumen 版本為7.x

[laravel/tinker](https://github.com/laravel/tinker) 是個強大的REPL Shell工具，Laravel 自帶這個工具，開發 Laravel 專案或多或少也應該都有使用過，而我個人已經習慣使用tinker來測試簡單或片段的程式。

今天心血來潮開了一個 Lumen 專案來玩玩，卻發現 Lumen 卻沒有內建tinker，但還好 Lumen 只是比較小的 Laravel，安裝tinker絕對不是問題。

## Lumen 安裝 `laravel/tinker`

使用 composer 安裝：

```shell
composer require laravel/tinker
```

## 註冊 Provider

Lumen 註冊 ServiceProvider 的方法是在 `bootstrap/app.php` 中註冊：

```php
$app->register(Laravel\Tinker\TinkerServiceProvider::class);
```

## 完成！
