# install

## composer install

[composer information](https://getcomposer.org/download/)
* 上記ページのCommand-line installationの手順通りに実行すればcomposer.pharファイルが作成されます。
このcomposer.pearをPATHの通ったディレクトリにcomposerとして移動します。

ex) ` $ mv composer.phar /usr/local/bin/composer`

ex) ` $ mv composer.phar $HOME/bin/composer`

なお、phpコードのcopyが使えない場合はwgetで代用してください。

```
$ wget https://getcomposer.org/installer
$ mv installer composer-setup.php
```

2行目以降はCommand-line installationの通りに進めてください。

## laravel5.8を新規作成する場合

* 最新のlaravelは6.xがリリースされているため古いバージョンをインストールする場合は下記のようにする

```
$ composer create-project --prefer-dist laravel/laravel [project-name] "5.8.*"
```

## 初期設定

```
$ git clone URL (or新規laravel project作成)
$ cd [project-name]
$ cp .env.example .env
$ vim .env
$ chmod 777 bootstrap/cahe/
$ find storage/ -type d |xargs chmod og+xw
$ touch storage/logs/laravel.log
$ chmod 666 storage/logs/laravel.log
$ composer install
$ php artisan key:generate
(必要があれば) $ php artisan migrate
```

## apache settings

* 前提条件

|  項目          | 説明 |
| -------------- | ----------------------------------------------------------- |
| apache version | 2.4系(2.2系の場合はそれに準拠した記載に読み替えてください)
| virtualhost    | example.com
| protocol       | http
| directory      | /path/to/dir

```
<VirtualHost *:80>
    ServerName example.com
    DocumentRoot /path/to/dir/public
    ErrorLog     logs/error_log
    CustomLog    logs/access_log combined
    <Directory "/path/to/dir/public">
        AllowOverride All
        Options Indexes FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
```

* nginxの設定は割愛
* 追加するファイルや場所は処理系により異なるのでそれぞれの環境に応して上記設定を追加してください
* SSL対応の場合は別途追加設定が必要ですが、証明書関連以外に必要な設定は上記となります

---

<p align="center"><img src="https://res.cloudinary.com/dtfbvvkyp/image/upload/v1566331377/laravel-logolockup-cmyk-red.svg" width="400"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## About Laravel

Laravel is a web application framework with expressive, elegant syntax. We believe development must be an enjoyable and creative experience to be truly fulfilling. Laravel takes the pain out of development by easing common tasks used in many web projects, such as:

- [Simple, fast routing engine](https://laravel.com/docs/routing).
- [Powerful dependency injection container](https://laravel.com/docs/container).
- Multiple back-ends for [session](https://laravel.com/docs/session) and [cache](https://laravel.com/docs/cache) storage.
- Expressive, intuitive [database ORM](https://laravel.com/docs/eloquent).
- Database agnostic [schema migrations](https://laravel.com/docs/migrations).
- [Robust background job processing](https://laravel.com/docs/queues).
- [Real-time event broadcasting](https://laravel.com/docs/broadcasting).

Laravel is accessible, powerful, and provides tools required for large, robust applications.

## Learning Laravel

Laravel has the most extensive and thorough [documentation](https://laravel.com/docs) and video tutorial library of all modern web application frameworks, making it a breeze to get started with the framework.

If you don't feel like reading, [Laracasts](https://laracasts.com) can help. Laracasts contains over 1500 video tutorials on a range of topics including Laravel, modern PHP, unit testing, and JavaScript. Boost your skills by digging into our comprehensive video library.

## Laravel Sponsors

We would like to extend our thanks to the following sponsors for funding Laravel development. If you are interested in becoming a sponsor, please visit the Laravel [Patreon page](https://patreon.com/taylorotwell).

- **[Vehikl](https://vehikl.com/)**
- **[Tighten Co.](https://tighten.co)**
- **[Kirschbaum Development Group](https://kirschbaumdevelopment.com)**
- **[64 Robots](https://64robots.com)**
- **[Cubet Techno Labs](https://cubettech.com)**
- **[Cyber-Duck](https://cyber-duck.co.uk)**
- **[British Software Development](https://www.britishsoftware.co)**
- **[Webdock, Fast VPS Hosting](https://www.webdock.io/en)**
- **[DevSquad](https://devsquad.com)**
- [UserInsights](https://userinsights.com)
- [Fragrantica](https://www.fragrantica.com)
- [SOFTonSOFA](https://softonsofa.com/)
- [User10](https://user10.com)
- [Soumettre.fr](https://soumettre.fr/)
- [CodeBrisk](https://codebrisk.com)
- [1Forge](https://1forge.com)
- [TECPRESSO](https://tecpresso.co.jp/)
- [Runtime Converter](http://runtimeconverter.com/)
- [WebL'Agence](https://weblagence.com/)
- [Invoice Ninja](https://www.invoiceninja.com)
- [iMi digital](https://www.imi-digital.de/)
- [Earthlink](https://www.earthlink.ro/)
- [Steadfast Collective](https://steadfastcollective.com/)
- [We Are The Robots Inc.](https://watr.mx/)
- [Understand.io](https://www.understand.io/)
- [Abdel Elrafa](https://abdelelrafa.com)
- [Hyper Host](https://hyper.host)

## Contributing

Thank you for considering contributing to the Laravel framework! The contribution guide can be found in the [Laravel documentation](https://laravel.com/docs/contributions).

## Security Vulnerabilities

If you discover a security vulnerability within Laravel, please send an e-mail to Taylor Otwell via [taylor@laravel.com](mailto:taylor@laravel.com). All security vulnerabilities will be promptly addressed.

## License

The Laravel framework is open-source software licensed under the [MIT license](https://opensource.org/licenses/MIT).
