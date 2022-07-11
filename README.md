# love-actions-linux

## About

Github Action for building & deploying Linux `.AppImage` packages of a [LÖVE](https://love2d.org/) framework based game.

### Related actions

See related actions below:

[Love actions bare package](https://github.com/marketplace/actions/love-actions-bare-package)
[Love actions for testing](https://github.com/marketplace/actions/love-actions-for-testing)
[Love actions for android](https://github.com/marketplace/actions/love-actions-for-android)
[Love actions for iOS](https://github.com/marketplace/actions/love-actions-for-ios)
[Love actions for macOS](https://github.com/marketplace/actions/love-actions-for-macos)
[Love actions for Windows](https://github.com/marketplace/actions/love-actions-for-windows)

## Quick example

```yaml
- name: Build Linux packages
  id: build-packages
  uses: 26F-Studio/love-actions-linux@main
  with:
    desktop-file-path: ./.github/build/linux/dev/template.desktop
    executable-name: app
    icon-path: ./.github/build/linux/dev/icon.png
    love-package: ${{ env.CORE_LOVE_PACKAGE_PATH }}
    product-name: ${{ steps.process-app-name.outputs.product-name }}
    output-folder: ${{ env.OUTPUT_FOLDER }}
```

## All inputs

| Name                      | Required | Default                | Description                                                  |
| :------------------------ | -------- | ---------------------- | ------------------------------------------------------------ |
| `desktop-file-path`               | `false`  | `""` | Path to the `.desktop` file, see [Desktop integration](https://docs.appimage.org/reference/desktop-integration.html). Use LÖVE default if not specified |
| `executable-name`          | `false`  | `"love"` | Executable name. Used as appImage's internal executable filename |
| `icon-path`          | `false`  | `""`                   | Path to the appImage's icon. Use LÖVE default if not specified |
| `love-package`         | `false`  | `"./game.love"`        | Love package. Used to assemble the executable |
| `product-name`   | `false`  | `"love_app"`           | Base name of the package. Used to rename products |
| `output-folder` | `false`  | `"./build"`            | Packages output folder. All packages would be placed here |

## All outputs

| Name            | Example                     | Description                                                  |
| :-------------- | --------------------------- | ------------------------------------------------------------ |
| `package-paths` | `./build/love_app.AppImage` | built packages' paths in a bash-style list relative to the repository root, separated by spaces |
