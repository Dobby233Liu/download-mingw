# download-mingw
Download a specific ray_linn style MinGW-w64 GCC build and then does everything for you.
Because `choco` is sour.

*Warning: this is Windows only, as is the toolchains. Use carefully and remember to configure enviourment variables (PATH/CC/CXX).*

# Usage
Simple, just use this:
```yaml
- uses: Dobby233Liu/download-mingw@main
```
Then just use the compiler **in it's location** as usual. You should configure `env`s for that to work with build systems.

# Output
`${{ outputs.path }}` is the path to GCC. The `bin` directory in it is what you want.
