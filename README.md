# download-mingw
Download a specific ray_linn style MinGW-w64 GCC build and then does everything else for you.
Because the `choco`late is sour.

*Warning: this is Windows only, as is the toolchains. Use carefully and remember to configure enviourment variables (PATH/CC/CXX).*

# Usage
Simple, have this in your steps:
```yaml
- uses: Dobby233Liu/download-mingw@main
```
(This solely downloads the compiler)

Then make sure that the steps that you want to use the downloaded compiler in actually uses the downloaded compiler (this is not done automatically). You should configure `env`s for that to work with build systems (see also [Output](#output)).

BONUS: path fix step
```yaml
    - name: fix path
      run: |
        set GITHUB_PATH="${{ steps.mingw.outputs.path }}\mingw64\bin;%GITHUB_PATH%"
        refreshenv
```
## Outputs
### `path`
Path to GCC. The `bin` directory in it is what you want if you run it.

So, for example:
```yaml
- uses: Dobby233Liu/download-mingw@main
  id: download-mingw
- run: |
    dir ${{ steps.download-mingw.outputs.path }}/bin/gcc.exe
    ${{ steps.download-mingw.outputs.path }}/bin/gcc.exe -v
```
Should not throw a error.

See also [action.yml](action.yml)

## Inputs
Normally you should not bother with these.

If you want to pin to a specific package, usually you should pin the commit.
The dest directory also should't matter too much.

### `path`
### `download-url`
See [action.yml](action.yml)
