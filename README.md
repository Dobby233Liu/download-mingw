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

Then just make (sure that) the steps that you desire to apply the downloaded compiler to actually use the downloaded compiler (this is not done automatically). You should configure `env`s for that to work with build systems (see also [Output](#output)).

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

# Input
Normally you should not bother with these.

If you want to pin to a specific package, usually you should pin the commit.
The dest directory also should't matter too much.

See [action.yml](action.yml)
