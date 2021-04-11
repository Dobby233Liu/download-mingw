# download-mingw
Download a specific ray_linn style MinGW-w64 GCC build and then does everything for you.
Because `choco` is sour.

*Warning: this is Windows only, as is the toolchains. Use carefully and remember to configure enviourment variables (PATH/CC/CXX).*

# Usage
Simple, just copy & paste this to your steps:
```yaml
- uses: Dobby233Liu/download-mingw@main
```
(This solely downloads the compiler)

Then just make (sure that) all the rest steps use the downloaded compiler (see also [Output](#output)). You should configure `env`s for that to work with build systems.

# Output
The output `${{ outputs.path }}` is the path to GCC. The `bin` directory in it is what you want.

So:
```yaml
- uses: Dobby233Liu/download-mingw@main
  id: download-mingw
- run: |
    dir ${{ steps.download-mingw.outputs.path }}/bin/gcc.exe
    ${{ steps.download-mingw.outputs.path }}/bin/gcc.exe -v
```
Should not throw a error.
