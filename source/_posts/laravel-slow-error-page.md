---
title: Laravel 錯誤頁面載入緩慢
date: 2020-04-09 18:13:06
uri: laravel-error-page-slow
categories:
- Laravel
tags:
- Laravel
---

> 在 Laravel 7 此問題應該已經不存在，Ignition 在 "^2.0" 已經將預設將 `collect_git_information` 設定為 `false` 了。

在 Laravel 6 迎來了全新的錯誤頁面，該錯誤頁面所使用的套件是 Ignition (GitHub: [facade/ignition](https://github.com/facade/ignition))。

工程師日常就是要除錯，每次看到漂亮的錯誤頁面，真是心花怒放。使用一陣子後發現錯誤頁面載入時間異常的緩慢，因此有同事提出替換掉 Ignition 套件，但我不願意回去看那醜醜的錯誤頁面，所以開始尋找 Ignition 載入緩慢的原因。

逛著官方文件，意外看到這個 [Customize error grouping](https://flareapp.io/docs/ignition-for-laravel/customize-error-grouping) ，該文件中寫到可以在 `config/flare.php` 進行一些錯誤頁面的設定:

```php
// config/flare.php
'reporting' => [
    'anonymize_ips' => true,
    'collect_git_information' => true,
    'report_queries' => true,
    'maximum_number_of_collected_queries' => 200,
    'report_query_bindings' => true,
    'report_view_data' => true,
    'grouping_type' => \Facade\FlareClient\Enums\GroupingTypes::EXCEPTION,
],
```

而其中 `'collect_git_information' => true,` 這個設定讓我非常困惑，不明白為何PHP的錯誤會與Git有關係，所以我決定把它關掉。

```bash
php artisan vendor:publish --tag=flare-config
```

將 Config Publish 後把 `collect_git_information` 設定為 `false`，然後隨便把程式弄壞來測試，錯誤頁面就如以前一樣迅速了🎉🎉
