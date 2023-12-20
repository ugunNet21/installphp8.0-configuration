<div align="center">
    <a href="https://php.net">
        <img
            alt="PHP"
            src="https://www.php.net/images/logos/new-php-logo.svg"
            width="150">
    </a>
</div>

# The PHP Interpreter

PHP is a popular general-purpose scripting language that is especially suited to
web development. Fast, flexible and pragmatic, PHP powers everything from your
blog to the most popular websites in the world. PHP is distributed under the
[PHP License v3.01](LICENSE).

[![Build status](https://travis-ci.org/php/php-src.svg?branch=master)](https://travis-ci.org/php/php-src)
[![Build status](https://ci.appveyor.com/api/projects/status/meyur6fviaxgdwdy/branch/master?svg=true)](https://ci.appveyor.com/project/php/php-src)
[![Build Status](https://dev.azure.com/phpazuredevops/php/_apis/build/status/php.php-src?branchName=master)](https://dev.azure.com/phpazuredevops/php/_build/latest?definitionId=1&branchName=master)
[![Fuzzing Status](https://oss-fuzz-build-logs.storage.googleapis.com/badges/php.svg)](https://bugs.chromium.org/p/oss-fuzz/issues/list?sort=-opened&can=1&q=proj:php)

## Documentation

The PHP manual is available at [php.net/docs](https://php.net/docs).

## Installation
# Cara Mengkonfigurasi PHP di Windows 10-11

1. **Download PHP:**
   Unduh PHP dari [situs resmi](link_download_php) dan dalam tutorial ini, kita akan menggunakan PHP 8.0. Pilih opsi seperti yang ditunjukkan pada gambar:

   ![Download PHP](link_gambar_download_php)

2. **Ekstrak ke Direktori Path:**
   Ekstrak file ZIP ke direktori path, misalnya `C:\src\php.8.0`.

3. **Buat Environment Path:**
   Buat environment path sesuai dengan direktori path pada langkah sebelumnya (`C:\src\php.8.0`). Lihat gambar untuk panduan.

4. **Cek Versi PHP:**
   Jalankan perintah `php -v` untuk memeriksa versi PHP yang telah diinstal. Hasilnya seharusnya sesuai dengan gambar yang diberikan.

5. **Konfigurasi PHP:**
   - Buka direktori path yang telah ditentukan pada langkah sebelumnya.
   - Cari file `php.ini-development`, ubah namanya menjadi `php.ini`.
   - Buka `php.ini` dengan menggunakan code editor (misalnya Notepad).
   - Cari dan uncomment (hilangkan tanda ; di depan) file-file berikut:
      ```ini
      extension=curl
      extension=fileinfo
      extension=gd
      extension=mbstring
      extension=mysqli
      extension=openssl
      extension=pdo_mysql
      ```
   - Alternatifnya, tekan `Ctrl+F` untuk mencari salah satu dari extension tersebut dan hilangkan tanda ; dari awal barisnya.
   - Terakhir, tambahkan direktori path PHP yang telah didaftarkan di environment, contohnya: `extension_dir = "C:\src\php8.0\ext"`. Tambahkan di antara daftar extension yang di-uncomment tadi. Pastikan direktori path-nya sesuai.

6. **Buat File `phpinfo.php`:**
   - Buat file `phpinfo.php` di dalam direktori path PHP (contoh: `C:\src\php.8.0`).
   - Isi file tersebut dengan:
      ```php
      <?php
      phpinfo();
      ```

7. **Selesai:**
   - Jika diperlukan, instal Composer.
   - Anda dapat menggunakan MAMP untuk Windows. XAMPP sering mengalami crash, tetapi ini terserah pilihan Anda. Jika menggunakan XAMPP, Anda tidak perlu menginstal PHP secara terpisah karena paketnya sudah lengkap. Anda hanya perlu menginstal Composer.

> Catatan: Pastikan untuk mengganti [link_download_php] dan [link_gambar_download_php] dengan tautan yang sesuai.


### Prebuilt packages and binaries

Prebuilt packages and binaries can be used to get up and running fast with PHP.

For Windows, the PHP binaries can be obtained from
[windows.php.net](https://windows.php.net). After extracting the archive the
`*.exe` files are ready to use.

For other systems, see the [installation chapter](https://php.net/install).

### Building PHP source code

*For Windows, see [Build your own PHP on Windows](https://wiki.php.net/internals/windows/stepbystepbuild_sdk_2).*

For a minimal PHP build from Git, you will need autoconf, bison, and re2c. For
a default build, you will additionally need libxml2 and libsqlite3. On Ubuntu,
you can install these using:

    sudo apt install -y pkg-config build-essential autoconf bison re2c \
                        libxml2-dev libsqlite3-dev

Generate configure:

    ./buildconf

Configure your build. `--enable-debug` is recommended for development, see
`./configure --help` for a full list of options.

    # For development
    ./configure --enable-debug
    # For production
    ./configure

Build PHP. To speed up the build, specify the maximum number of jobs using `-j`:

    make -j4

The number of jobs should usually match the number of available cores, which
can be determined using `nproc`.

## Testing PHP source code

PHP ships with an extensive test suite, the command `make test` is used after
successful compilation of the sources to run this test suite.

It is possible to run tests using multiple cores by setting `-jN` in
`TEST_PHP_ARGS`:

    make TEST_PHP_ARGS=-j4 test

Shall run `make test` with a maximum of 4 concurrent jobs: Generally the maximum
number of jobs should not exceed the number of cores available.

The [qa.php.net](https://qa.php.net) site provides more detailed info about
testing and quality assurance.

## Installing PHP built from source

After a successful build (and test), PHP may be installed with:

    make install

Depending on your permissions and prefix, `make install` may need super user
permissions.

## PHP extensions

Extensions provide additional functionality on top of PHP. PHP consists of many
essential bundled extensions. Additional extensions can be found in the PHP
Extension Community Library - [PECL](https://pecl.php.net).

## Contributing

The PHP source code is located in the Git repository at
[github.com/php/php-src](https://github.com/php/php-src). Contributions are most
welcome by forking the repository and sending a pull request.

Discussions are done on GitHub, but depending on the topic can also be relayed
to the official PHP developer mailing list internals@lists.php.net.

New features require an RFC and must be accepted by the developers. See
[Request for comments - RFC](https://wiki.php.net/rfc) and
[Voting on PHP features](https://wiki.php.net/rfc/voting) for more information
on the process.

Bug fixes don't require an RFC. If the bug has a GitHub issue, reference it in
the commit message using `GH-NNNNNN`. Use `#NNNNNN` for tickets in the old
[bugs.php.net](https://bugs.php.net) bug tracker.

    Fix GH-7815: php_uname doesn't recognise latest Windows versions
    Fix #55371: get_magic_quotes_gpc() throws deprecation warning

See [Git workflow](https://wiki.php.net/vcs/gitworkflow) for details on how pull
requests are merged.

### Guidelines for contributors

See further documents in the repository for more information on how to
contribute:

- [Contributing to PHP](/CONTRIBUTING.md)
- [PHP coding standards](/CODING_STANDARDS.md)
- [Mailinglist rules](/docs/mailinglist-rules.md)
- [PHP release process](/docs/release-process.md)

## Credits

For the list of people who've put work into PHP, please see the
[PHP credits page](https://php.net/credits.php).
