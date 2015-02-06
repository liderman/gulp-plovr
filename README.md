# gulp-plovr
> Gulp plugin. Wrapper for Plovr (Closure build tool)

This is a simple wrapper for Plovr.

### Table of Contents

- [Install](#install)
- [Options](#options)
- [Example usage](#example-usage)

## Install

```shell
npm install --save-dev gulp-plovr
```

## Options

  - `debug` (Boolean)
  
    Option log to console. In debug mode will be displayed warning.
    This option is disabled by default.

    Enabling debug mode:
    ```js
        ...

        .pipe(gulpPlovr({debug: true}))

        ...
    ```

  - `plovr_path` (String)

    Absolute path to the jar-file Plovr.
    Used by default file: plovr-81ed862.jar (release date is Jul 29, 2013)
    https://code.google.com/p/plovr/downloads/detail?name=plovr-81ed862.jar&can=2&q=

  - `java_path` (String)

    Path to the interpreter java.
    Default value: java

  - `plovr_args` (Object)

    Arguments are the command line.

    Example of argument passing "--formatting=PRETTY_PRINT":
    ```js
        ...

        .pipe(
          gulpPlovr({
            plovr_args: {"formatting": "PRETTY_PRINT"}
          })
        )

        ...
    ```

## Example usage

This example is similar to executing the command in the console:
    ```shell
        java -jar plovr-81ed862.jar build ./closure-compiler-plovr-config.json
    ```

    Equivalent to gulp:
    ```js
        var plovr = require('gulp-plovr');
        gulp.task('jsbuild', function() {
          return gulp.src(['./closure-compiler-plovr-config.json'])
            .pipe(plovr({
              debug: true
            }));
        });
    ```
