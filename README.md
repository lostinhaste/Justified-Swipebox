# Justified Swipebox - Hugo Plugin for Micro.blog 🎞️
Inspired by [GLightbox](https://github.com/jsonbecker/plugin-glightbox), a lovely image Hugo plugin created by [@jsonbecker](https://micro.blog/jsonbecker), Justified Swipebox is a plugin for [Micro.blog](https://micro.blog/) to _easily_ allow the creation of "clickable" image galleries on posts and pages. It depends on the [Justified Gallery](https://github.com/miromannino/Justified-Gallery) to create the initial gallery on the post/page and [Swipebox](https://github.com/brutaldesign/swipebox) to show the image(s) at a larger resolution when an item in the gallery is clicked / touched. This plugin wouldn't exist without either of those projects, as it's just combining the two of them to work properly in the Micro.blog plugin system. 👏🏻

![Main Image for Project](https://raw.githubusercontent.com/lostinhaste/Justified-Swipebox/main/documentation/main-image.png)

_**Note:**_ The markdown preview in the Micro.blog plugin-in system doesn't seem to handle multi-line code blocks _or_ tables. It is advisable view this document on [Github](https://github.com/lostinhaste/Justified-Swipebox/blob/main/README.md) or in a dedicated Markdown viewer.

## How To Use
The plugin supplies two shortcodes, one for each image and one to call the required JavaScript (`justified-swipebox-entry` and `justified-swipebox-gallery`); essentially it's one to many `justified-swipebox-entry` shortcodes and `justified-swipebox-gallery` (per gallery).

The following code...
```go
<div id="gardenGlow2023" class="justified-gallery">
   {{< justified-swipebox-entry photo="https://lostinhaste.com/uploads/2023/garden-glow-01-full.jpg" >}}
   {{< justified-swipebox-entry photo="https://lostinhaste.com/uploads/2023/garden-glow-02-full.jpg" >}}
   {{< justified-swipebox-entry photo="https://lostinhaste.com/uploads/2023/garden-glow-03-full.jpg" >}}
   {{< justified-swipebox-entry photo="https://lostinhaste.com/uploads/2023/garden-glow-04-full.jpg" >}}
<div>

{{< justified-swipebox-gallery id="gardenGlow2023" rowHeight="200" >}}
```
...will result in something like this (depending on the template / theme you're using):

![Example 1](https://raw.githubusercontent.com/lostinhaste/Justified-Swipebox/main/documentation/example-1.png)

Each gallery should be wrapped in a `div` with a class of _"justified-gallery"_. Multiple galleries are possible per page but the _id_ of the holding `div` needs to match the _gallery_ for each `justified-swipebox-entry` shortcode along with the the _id_ `justified-swipebox-gallery` shortcode.

### ⚠️ Warning! ⚠️
There appears to be some bug somewhere in the Micro.blog system, preventing this plugin from working properly if extra lines (_carriage returns_, for those of us old enough to remember that term) are contained within the `div`, the plugin will not work properly. Even if there is a line break between the `div` (the one containing the _"justified-gallery"_ class) and the first `justified-swipebox-entry` entry, the plugin might fail.

## Parameter List / Key

Below are a list of the various parameters the Plugin can use when generating HTML, broken down by shortcode.

### `justified-swipebox-entry`

| Parameter | Required | Description |
|---|---|---|
| `photo` | Yes | Link to the image. |
| `thumbnail` | No | Link to a thumbnail version of the image, for faster loading. |
| `title` | No | Text that is shown when the full resolution of an image is shown. |
| `alt` | No | Alternative text to be included in the generated `img` tag. |
| `gallery` | No | Required if multiple galleries are to be loaded, it should match the _id_ of the holding `div` and the _id_ `justified-swipebox-gallery` shortcode. |

### `justified-swipebox-gallery`

| Parameter | Required | Description |
|---|---|---|
| `id` | Yes | CSS selector to the `div` containing the `justified-swipebox-entry` entries. |
| `margin` | No | Defaults to `3`, it is the _margin_ (in pixels) between images in the gallery |
| `showCaptionsOnHover` | No | Defaults to `false`, if `true`, when a user hovers over an image in the gallery, the _title_ / _alt_ text will be shown. |


## Change Logs

| Version | Date | Description |
|---|---|---|
| 1.0.2 | January 12, 2024 | Adding text to the Micro.blog description so the Plugin is picked up in the _Photos_ section in the Micro.blog plugin system. |
| 1.0.1 | January 12, 2024 | Updating the Read Me file: more credit to the supporting libraries, added a note about viewing the Read Me file, and added a warning about spacing issues. |
| 1.0.0 | December 15, 2023 | The initial release of the project. |