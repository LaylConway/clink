# Clink
A simple C++ build system generator. Simplify your Visual Studio project linking.

## Getting Started
1. Download clink.exe from github releases.
2. Place it somewhere in your PATH system variable.
3. Run `clink init` in every project folder you want, edit the created
    *Clink.toml* files to what you want those projects to be.
4. Navigate a command shell to the clink project folder you want to use as root
    to generate the project and solution files for.
5. Run `clink` in your command shell.

Clink expects your *.hpp*/*.h* files to be in the */include* directory. You can
add new files from within Visual Studio, but they will not automatically be
placed in the folder associated with a filter, you need to do this manually when
creating the file.

### Example *Clink.toml* files
```toml
[package]
name = "MyGame"
type = "application"

[dependencies]
AmazingEngine = "../../Engine/Libraries/AmazingEngine"
```

```toml
[package]
name = "AmazingEngine"
type = "library"

[dependencies]
```

## Filter-only Usage
You can also use clink to only generate a *.vcxproj.filters* file. Keep in mind
that when doing this, clink will not update your *.vcxproj* with new or moved
files, it will only re-order them in filters. The best way to work with this is
to **add files from within Visual Studio** and re-run `clink filters` if you
need to add folders or fix mistakes.

1. Follow steps 1-4 from **Getting Started**. You can omit dependencies if you
    plan to only use clink for filters.
2. **Make sure you have a Clink.toml file with a name matching the project you
    want to generate for.**
3. Run `clink filters` in your command shell in the project folder you want to
    generate Visual Studio filters for.
4. Reload your project in Visual Studio. (This is unfortunately needed because
    Visual Studio does not detect changes to the filters file)
5. (Optional) Create a .cmd file or build event to automatically generate
    filters. Clink-filters will not automatically generate filters for
    dependencies, it assumes you do not want to use the dependency system.

## License
Licensed under either of
 * Apache License, Version 2.0 ([LICENSE-APACHE](LICENSE-APACHE) or http://www.apache.org/licenses/LICENSE-2.0)
 * MIT license ([LICENSE-MIT](LICENSE-MIT) or http://opensource.org/licenses/MIT)

at your option.
