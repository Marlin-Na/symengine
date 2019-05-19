
## Dependencies and built artifacts needed for building R package on windows

### Symengine artifacts from appveyor

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

