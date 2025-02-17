**This fork (`fix_openblas` branch) is a custom repository that contains a fix for the `OpenBlas` build error.**<br>
**See: https://zenn.dev/pinto0309/scraps/072fe73c6011c8**<br>
**Kaldi forked from: [1a233a11db](https://github.com/kaldi-asr/kaldi/tree/1a233a11db0b28aa4966a4e271c839c135de5914)**<br>
```bash
/usr/include/lapack.h:15908:6: note: declared here
15908 | void LAPACK_ssptrf_base(
      |      ^~~~~~~~~~~~~~~~~~
In file included from ../matrix/jama-svd.h:34,
                 from kaldi-matrix.cc:27:
../matrix/cblas-wrappers.h: In function 'void kaldi::clapack_Xsptrf(KaldiBlasInt*, double*, KaldiBlasInt*, KaldiBlasInt*)':
../matrix/cblas-wrappers.h:451:10: error: too few arguments to function 'void dsptrf_(const char*, const int*, double*, int*, int*, size_t)'
  451 |   dsptrf_(const_cast<char *>("U"), num_rows, Mdata, ipiv, result);
      |   ~~~~~~~^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
In file included from /usr/include/lapack.h:11,
                 from /usr/include/lapacke.h:36,
                 from ../matrix/kaldi-blas.h:100,
                 from ../matrix/cblas-wrappers.h:29,
                 from ../matrix/jama-svd.h:34,
                 from kaldi-matrix.cc:27:
/usr/include/lapack.h:15892:6: note: declared here
15892 | void LAPACK_dsptrf_base(
      |      ^~~~~~~~~~~~~~~~~~
make[1]: *** [<builtin>: tp-matrix.o] Error 1
make[1]: *** Waiting for unfinished jobs....
make[1]: *** [<builtin>: qr.o] Error 1
make[1]: *** [<builtin>: packed-matrix.o] Error 1
make[1]: *** [<builtin>: sp-matrix.o] Error 1
make[1]: *** [<builtin>: kaldi-vector.o] Error 1
make[1]: *** [<builtin>: kaldi-matrix.o] Error 1
make[1]: Leaving directory '/workdir/kaldi/src/matrix'
make: *** [Makefile:164: matrix] Error 2
```
================================


[![Build Status](https://travis-ci.com/kaldi-asr/kaldi.svg?branch=master)](https://travis-ci.com/kaldi-asr/kaldi)
[![Gitpod Ready-to-Code](https://img.shields.io/badge/Gitpod-Ready--to--Code-blue?logo=gitpod)](https://gitpod.io/#https://github.com/kaldi-asr/kaldi) 
Kaldi Speech Recognition Toolkit
================================

To build the toolkit: see `./INSTALL`.  These instructions are valid for UNIX
systems including various flavors of Linux; Darwin; and Cygwin (has not been
tested on more "exotic" varieties of UNIX).  For Windows installation
instructions (excluding Cygwin), see `windows/INSTALL`.

To run the example system builds, see `egs/README.txt`

If you encounter problems (and you probably will), please do not hesitate to
contact the developers (see below). In addition to specific questions, please
let us know if there are specific aspects of the project that you feel could be
improved, that you find confusing, etc., and which missing features you most
wish it had.

Kaldi information channels
--------------------------

For HOT news about Kaldi see [the project site](http://kaldi-asr.org/).

[Documentation of Kaldi](http://kaldi-asr.org/doc/):
- Info about the project, description of techniques, tutorial for C++ coding.
- Doxygen reference of the C++ code.

[Kaldi forums and mailing lists](http://kaldi-asr.org/forums.html):

We have two different lists
- User list kaldi-help
- Developer list kaldi-developers:

To sign up to any of those mailing lists, go to
[http://kaldi-asr.org/forums.html](http://kaldi-asr.org/forums.html):


Development pattern for contributors
------------------------------------

1. [Create a personal fork](https://help.github.com/articles/fork-a-repo/)
   of the [main Kaldi repository](https://github.com/kaldi-asr/kaldi) in GitHub.
2. Make your changes in a named branch different from `master`, e.g. you create
   a branch `my-awesome-feature`.
3. [Generate a pull request](https://help.github.com/articles/creating-a-pull-request/)
   through the Web interface of GitHub.
4. As a general rule, please follow [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html).
   There are a [few exceptions in Kaldi](http://kaldi-asr.org/doc/style.html).
   You can use the [Google's cpplint.py](https://raw.githubusercontent.com/google/styleguide/gh-pages/cpplint/cpplint.py)
   to verify that your code is free of basic mistakes.

Platform specific notes
-----------------------

### PowerPC 64bits little-endian (ppc64le)

- Kaldi is expected to work out of the box in RHEL >= 7 and Ubuntu >= 16.04 with
  OpenBLAS, ATLAS, or CUDA.
- CUDA drivers for ppc64le can be found at [https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads).
- An [IBM Redbook](https://www.redbooks.ibm.com/abstracts/redp5169.html) is
  available as a guide to install and configure CUDA.

### Android

- Kaldi supports cross compiling for Android using Android NDK, clang++ and
  OpenBLAS.
- See [this blog post](http://jcsilva.github.io/2017/03/18/compile-kaldi-android/)
  for details.

### Web Assembly

- Kaldi supports cross compiling for Web Assembly for in-browser execution
  using [emscripten](https://emscripten.org/) and CLAPACK.
- See [this post](https://gitlab.inria.fr/kaldi.web/kaldi-wasm/-/wikis/build_details.md)
  for a step-by-step description of the build process.
