# download-mingw
Download a specific ray_linn style MinGW-w64 GCC build and then does everything else for you.
Because the `choco`late is sour.

*Warning: this is Windows only, as is the toolchains. Use carefully and remember that there always are some annoyances with the build. (`make` might not work!)*

# Usage
Simple, have this in your steps:
```yaml
- uses: Dobby233Liu/download-mingw@main
```
(This solely downloads the compiler)

That's all. Just use GCC happliy.

## Outputs

### `path`
The path to the downloaded compiler.

See also [action.yml](action.yml)

## Inputs
Normally, you should not bother with these.

If you want to pin to a specific package, usually you should pin the commit.
The destination directory should't matter too much either.

### `path`
### `download-url`

See [action.yml](action.yml)

# EXTRA: why is `choco` sour for me
Because it is slow. SO, SOOOO SLOOOOOOOW. Even just downloading a f\*\*king `mingw` takes about 5 mins in Github Actions' hosted runner. I wonder WTF it's even doing in "the pre-warming phase". Also, caches doesn't work for me, and what it downloads for `mingw` is not multi-arch. It's hard to bear with it. I have no choice. So for the f\*\*k's sake I made this. A whooping 20s, then everything just works. Fits all of my needs, with zero further pain. Here you go.
