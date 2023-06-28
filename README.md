# Futhak-Bloom

## Building

1. Set up the [ZMK Toolchain](https://zmk.dev/docs/development/setup).

2. Clone this repository within the ZMK repository.

3. Activate the Python virtual environment in which `west` has been set up.

4. From ZMK's `app` directory, run the build command:

```sh
west build -p -d build/right-lily -b nice_nano_v2 -- -DSHIELD=lily58_right -DZMK_CONFIG="../futhak-bloom/config"
west build -p -d build/left-lily -b nice_nano_v2 -- -DSHIELD=lily58_left -DZMK_CONFIG="../futhak-bloom/config"
```

This can also used to generate the `settings_reset` binary:

```sh
west build -p -d build/right-reset -b nice_nano_v2 -- -DSHIELD=settings_reset -DZMK_CONFIG="../futhak-bloom/config"
west build -p -d build/left-reset -b nice_nano_v2 -- -DSHIELD=settings_reset -DZMK_CONFIG="../futhak-bloom/config"
```

After building for the first time, the build speed can be improved by using
just the cached content of the build directory.

```sh
west build -d build/right-lily
west build -d build/left-lily
```

The resulting configs can be quickly copied to this repository:

```sh
cp build/left-lily/zephyr/zmk.uf2 ../futhak-bloom/left-lily.uf2
cp build/right-lily/zephyr/zmk.uf2 ../futhak-bloom/right-lily.uf2
cp build/left-reset/zephyr/zmk.uf2 ../futhak-bloom/left-reset.uf2
cp build/right-reset/zephyr/zmk.uf2 ../futhak-bloom/right-reset.uf2
```
