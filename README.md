<!--

@license Apache-2.0

Copyright (c) 2024 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# dspmv

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Perform the matrix-vector operation `y = α*A*x + β*y` where `α` and `β` are scalars, `x` and `y` are `N` element vectors and, `A` is an `N` by `N` symmetric matrix supplied in packed form.



<section class="usage">

## Usage

To use in Observable,

```javascript
dspmv = require( 'https://cdn.jsdelivr.net/gh/stdlib-js/blas-base-dspmv@v0.1.1-umd/browser.js' )
```

To vendor stdlib functionality and avoid installing dependency trees for Node.js, you can use the UMD server build:

```javascript
var dspmv = require( 'path/to/vendor/umd/blas-base-dspmv/index.js' )
```

To include the bundle in a webpage,

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/blas-base-dspmv@v0.1.1-umd/browser.js"></script>
```

If no recognized module system is present, access bundle contents via the global scope:

```html
<script type="text/javascript">
(function () {
    window.dspmv;
})();
</script>
```

#### dspmv( order, uplo, N, α, AP, x, sx, β, y, sy )

Performs the matrix-vector operation `y = α*A*x + β*y` where `α` and `β` are scalars, `x` and `y` are `N` element vectors, and `A` is an `N` by `N` symmetric matrix supplied in packed form `AP`.

```javascript
var Float64Array = require( '@stdlib/array-float64' );

var AP = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var x = new Float64Array( [ 1.0, 1.0, 1.0 ] );
var y = new Float64Array( [ 1.0, 1.0, 1.0 ] );

dspmv( 'column-major', 'lower', 3, 1.0, AP, x, 1, 1.0, y, 1 );
// y => <Float64Array>[ 7.0, 12.0, 15.0 ]
```

The function has the following parameters:

-   **order**: storage layout.
-   **uplo**: specifies whether the upper or lower triangular part of the symmetric matrix `A` is supplied.
-   **N**: specifies the order of the matrix `A`.
-   **α**: scalar constant.
-   **AP**: packed form of a symmetric matrix `A` stored in linear memory as a [`Float64Array`][mdn-float64array].
-   **x**: input [`Float64Array`][mdn-float64array].
-   **sx**: index increment for `x`.
-   **β**: scalar constant.
-   **y**: output [`Float64Array`][mdn-float64array].
-   **sy**: index increment for `y`.

The stride parameters determine how elements in the input arrays are accessed at runtime. For example, to iterate over the elements of `y` in reverse order,

```javascript
var Float64Array = require( '@stdlib/array-float64' );

var AP = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var x = new Float64Array( [ 1.0, 1.0, 1.0 ] );
var y = new Float64Array( [ 1.0, 1.0, 1.0 ] );

dspmv( 'column-major', 'lower', 3, 1.0, AP, x, 1, 1.0, y, -1 );
// y => <Float64Array>[ 15.0, 12.0, 7.0 ]
```

Note that indexing is relative to the first index. To introduce an offset, use [`typed array`][mdn-typed-array] views.

<!-- eslint-disable stdlib/capitalized-comments -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );

// Initial arrays...
var x0 = new Float64Array( [ 0.0, 1.0, 1.0 ] );
var y0 = new Float64Array( [ 0.0, 1.0, 1.0 ] );
var AP = new Float64Array( [ 1.0, 2.0, 3.0 ] );

// Create offset views...
var x1 = new Float64Array( x0.buffer, x0.BYTES_PER_ELEMENT*1 ); // start at 2nd element
var y1 = new Float64Array( y0.buffer, y0.BYTES_PER_ELEMENT*1 ); // start at 2nd element

dspmv( 'row-major', 'upper', 2, 1.0, AP, x1, -1, 1.0, y1, -1 );
// y0 => <Float64Array>[ 0.0, 6.0, 4.0 ]
```

#### dspmv.ndarray( order, uplo, N, α, AP, oa, x, sx, ox, β, y, sy, oy )

Performs the matrix-vector operation `y = α*A*x + β*y` using alternative indexing semantics and where `α` and `β` are scalars, `x` and `y` are `N` element vectors, and `A` is an `N` by `N` symmetric matrix supplied in packed form `AP`.

```javascript
var Float64Array = require( '@stdlib/array-float64' );

var AP = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var x = new Float64Array( [ 1.0, 1.0, 1.0 ] );
var y = new Float64Array( [ 1.0, 1.0, 1.0 ] );

dspmv.ndarray( 'column-major', 'lower', 3, 1.0, AP, 0, x, 1, 0, 1.0, y, 1, 0 );
// y => <Float64Array>[ 7.0, 12.0, 15.0 ]
```

The function has the following additional parameters:

-   **oa**: starting index for `AP`.
-   **ox**: starting index for `x`.
-   **oy**: starting index for `y`.

While [`typed array`][mdn-typed-array] views mandate a view offset based on the underlying buffer, the offset parameters support indexing semantics based on starting indices. For example,

```javascript
var Float64Array = require( '@stdlib/array-float64' );

var AP = new Float64Array( [ 0.0, 0.0, 1.0, 2.0, 3.0, 4.0, 5.0, 6.0 ] );
var x = new Float64Array( [ 1.0, 1.0, 1.0 ] );
var y = new Float64Array( [ 1.0, 1.0, 1.0 ] );

dspmv.ndarray( 'column-major', 'lower', 3, 1.0, AP, 2, x, 1, 0, 1.0, y, -1, 2 );
// y => <Float64Array>[ 15.0, 12.0, 7.0 ]
```

</section>

<!-- /.usage -->

<section class="notes">

## Notes

-   `dspmv()` corresponds to the [BLAS][blas] level 2 function [`dspmv`][dspmv].

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/random-array-discrete-uniform@umd/browser.js"></script>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/blas-base-dspmv@v0.1.1-umd/browser.js"></script>
<script type="text/javascript">
(function () {

var opts = {
    'dtype': 'float64'
};

var N = 3;
var AP = discreteUniform( N * ( N + 1 ) / 2, -10, 10, opts );

var x = discreteUniform( N, -10, 10, opts );
var y = discreteUniform( N, -10, 10, opts );

dspmv.ndarray( 'row-major', 'upper', N, 1.0, AP, 0, x, 1, 0, 1.0, y, 1, 0 );
console.log( y );

})();
</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->



<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2026. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/blas-base-dspmv.svg
[npm-url]: https://npmjs.org/package/@stdlib/blas-base-dspmv

[test-image]: https://github.com/stdlib-js/blas-base-dspmv/actions/workflows/test.yml/badge.svg?branch=v0.1.1
[test-url]: https://github.com/stdlib-js/blas-base-dspmv/actions/workflows/test.yml?query=branch:v0.1.1

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/blas-base-dspmv/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/blas-base-dspmv?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/blas-base-dspmv.svg
[dependencies-url]: https://david-dm.org/stdlib-js/blas-base-dspmv/main

-->

[chat-image]: https://img.shields.io/badge/zulip-join_chat-brightgreen.svg
[chat-url]: https://stdlib.zulipchat.com

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/blas-base-dspmv/tree/deno
[deno-readme]: https://github.com/stdlib-js/blas-base-dspmv/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/blas-base-dspmv/tree/umd
[umd-readme]: https://github.com/stdlib-js/blas-base-dspmv/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/blas-base-dspmv/tree/esm
[esm-readme]: https://github.com/stdlib-js/blas-base-dspmv/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/blas-base-dspmv/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/blas-base-dspmv/main/LICENSE

[blas]: http://www.netlib.org/blas

[dspmv]: https://www.netlib.org/lapack/explore-html/d0/d4b/group__hpmv_ga739f8dc2316523832bde2b237fcad8a6.html#ga739f8dc2316523832bde2b237fcad8a6

[mdn-float64array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Float64Array

[mdn-typed-array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray

</section>

<!-- /.links -->
