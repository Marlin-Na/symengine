
## Dependencies and built artifacts needed for building R package on windows

### Compiled symengine library from appveyor

Currently they are built with MinGw-w64 in this repository for i686 and x86_64 as static library, without mpfr and mpc support:
  - `Environment: BUILD_TYPE=Release, COMPILER=rdep-x64-MinGW-w64, PLATFORM=x64, LIB_TYPE=lib`
  - `Environment: BUILD_TYPE=Release, COMPILER=rdep-i686-MinGW-w64, PLATFORM=x64, LIB_TYPE=lib`

```
wget -O symengine-32.zip https://ci.appveyor.com/api/buildjobs/tpqbsyounttxb9r1/artifacts/symengine_rdep-i686-MinGW-w64_x64.zip
wget -O symengine-64.zip https://ci.appveyor.com/api/buildjobs/xqksg0cmubkvks56/artifacts/symengine_rdep-x64-MinGW-w64_x64.zip
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

### MinGW-w64

I bundled the MinGW-w64 toolchains for x86_64 and i686 targets.
They are copied from installation directory of Rtools version 3.5.0.4.

