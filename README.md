
## Dependencies and built artifacts needed for building R package on windows

### Compiled symengine library from appveyor

The build is currently derived from commit `[4733e429883aad551138a607f2a5a40f73920f02](https://github.com/symengine/symengine/tree/4733e429883aad551138a607f2a5a40f73920f02)`.
The current options are (built as shared library, without mpfr and mpc support):
  - `Environment: BUILD_TYPE=Release, COMPILER=MinGW, PLATFORM=Win32, LIB_TYPE=dll`
  - `Environment: BUILD_TYPE=Release, COMPILER=MinGW-w64, PLATFORM=x64, LIB_TYPE=dll`

```
wget -O symengine-32.zip https://ci.appveyor.com/api/buildjobs/tsua4v1i9oalcnvb/artifacts/symengine_MinGW_Win32.zip
wget -O symengine-64.zip https://ci.appveyor.com/api/buildjobs/2qdywq1h6t93ln92/artifacts/symengine_MinGW-w64_x64.zip
```


### GMP

They are currently copied from [here](https://github.com/symengine/dependencies/tree/binaries)
but re-packed as `zip` format which is supported in R.

```
wget -O gmp-64.7z https://github.com/symengine/dependencies/raw/binaries/gmp-6.0.0-x86_64-w64-mingw32.7z
mkdir tmp && 7z x gmp-64.7z -otmp && 7z a gmp-64.zip ./tmp/* && rm -rf tmp

wget -O gmp-32.7z https://github.com/symengine/dependencies/raw/binaries/gmp-6.0.0-i686-w64-mingw32.7z
mkdir tmp && 7z x gmp-32.7z -otmp && 7z a gmp-32.zip ./tmp/* && rm -rf tmp

rm gmp-32.7z gmp-64.7z
```

