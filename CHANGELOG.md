# CHANGELOG

> Package changelog.

<section class="release" id="v0.1.0">

## 0.1.0 (2026-01-31)

<section class="features">

### Features

-   [`bc23559`](https://github.com/stdlib-js/stdlib/commit/bc2355981ffa28082d8e23273887501bd3ba674a) - add support for specifying the index offset for `AP`
-   [`ca56638`](https://github.com/stdlib-js/stdlib/commit/ca566387ddc147c4f15fd012a09bd55713307394) - add `blas/base/dspmv` [(#2456)](https://github.com/stdlib-js/stdlib/pull/2456)

</section>

<!-- /.features -->

<section class="breaking-changes">

### BREAKING CHANGES

-   [`bc23559`](https://github.com/stdlib-js/stdlib/commit/bc2355981ffa28082d8e23273887501bd3ba674a): add offset parameter to `ndarray` method

    -   To migrate, users should set the `offsetAP` parameter. For most cases,
        this parameter will be zero, but supporting this parameter allows
        users to specify alternative starting indices, such as needed when
        working with ndarray views.

</section>

<!-- /.breaking-changes -->

<section class="commits">

### Commits

<details>

-   [`71fcdf5`](https://github.com/stdlib-js/stdlib/commit/71fcdf5cead762267457905a25443c287cdbaea6) - **refactor:** use base assertion utility _(by Athan Reines)_
-   [`e0cef99`](https://github.com/stdlib-js/stdlib/commit/e0cef995e884021db3001dc1a3cfef0ca7b368c2) - **style:** remove extra spaces for regular expressions in publish script _(by Philipp Burckhardt)_
-   [`fc54a2b`](https://github.com/stdlib-js/stdlib/commit/fc54a2b7f610c9e19715d2b2d6ef14c2b3736e5f) - **docs:** update examples _(by Athan Reines)_
-   [`bc23559`](https://github.com/stdlib-js/stdlib/commit/bc2355981ffa28082d8e23273887501bd3ba674a) - **feat:** add support for specifying the index offset for `AP` _(by Athan Reines)_
-   [`43b84f7`](https://github.com/stdlib-js/stdlib/commit/43b84f7b8614a31ed5985c010572da16b2b5186d) - **refactor:** use utility to resolve an index offset _(by Athan Reines)_
-   [`1654659`](https://github.com/stdlib-js/stdlib/commit/1654659445a6dee281706379770c9cb0498c36c7) - **refactor:** update implementation to reduce code duplication [(#2480)](https://github.com/stdlib-js/stdlib/pull/2480) _(by Aman Bhansali, Athan Reines)_
-   [`ca56638`](https://github.com/stdlib-js/stdlib/commit/ca566387ddc147c4f15fd012a09bd55713307394) - **feat:** add `blas/base/dspmv` [(#2456)](https://github.com/stdlib-js/stdlib/pull/2456) _(by Aman Bhansali, Athan Reines)_

</details>

</section>

<!-- /.commits -->

<section class="contributors">

### Contributors

A total of 3 people contributed to this release. Thank you to the following contributors:

-   Aman Bhansali
-   Athan Reines
-   Philipp Burckhardt

</section>

<!-- /.contributors -->

</section>

<!-- /.release -->

