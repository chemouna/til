
### Running android tests from the command line

- Rebuild both app package and test package by running assembleRelease or
  assemble whatever build type you want

- install them on device
  ```bash
   adb -s $deviceSerialNumber install -r $appApkPath
  ```
- run
    ```bash
    adb -s $deviceSerialNumber shell am instrument --no-window-animation -w
                    -e class $testClassName
    ```
Checkout other possible options [here](http://developer.android.com/tools/testing/testing_otheride.html) and [here](http://developer.android.com/tools/help/shell.html)
