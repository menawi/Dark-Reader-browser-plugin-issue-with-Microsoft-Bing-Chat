
> [!NOTE]
> - Dark Reader is a popular browser extension designed to improve the readability of websites by providing a dark mode or dark theme. It is available for various web browsers like Google Chrome, Mozilla Firefox, Microsoft Edge, and others.

## [Dark Reader Dev Tools](https://github.com/darkreader/darkreader/blob/ccc6f17ca98d53cf22155d54a6e805e1cb423a5a/CONTRIBUTING.md#how-to-use-the-dev-tools)

- See the actual documentation here [Dark Reader Dev Tools](https://github.com/darkreader/darkreader/blob/ccc6f17ca98d53cf22155d54a6e805e1cb423a5a/CONTRIBUTING.md#how-to-use-the-dev-tools). The following is a summary of the most important parts for this project. 

**Dark Reader Dev Tools** is a set of tools that allows you to modify specific page styling when using the Dark Reader extension. This documentation will guide you on how to use these tools effectively.

## `dynamic-theme-fixes.config`

The `dynamic-theme-fixes.config` file allows you to define custom styling rules for specific web pages. By creating rules in this configuration file, you can control how Dark Reader applies its dark mode to various elements on a webpage.

### Example Configuration:
```css
dynamic-theme-fixes.config
================================

example.com

INVERT
.icon

CSS
.wrong-element-colors {
    background-color: ${white} !important;
    color: ${black} !important;
}

IGNORE INLINE STYLE
.color-picker

IGNORE IMAGE ANALYSIS
.logo
```

## Rule Descriptions

In your configuration, you define rules to customize the way Dark Reader handles specific elements on web pages. Here's an overview of the available rules:

|Rule|Description|Notes / Examples|
|---|---|---|
|**INVERT**|Inverts specified elements.|**Dynamic Mode**: INVERT only for dark images that are invisible on dark backgrounds.|
|**CSS**|Adds custom CSS to a web page.|`!important` keyword should be specified for each CSS property to prevent overrides by other stylesheets.  <br>**Dynamic mode** supports `${COLOR}` template, where `COLOR` is a color value before the inversion.  <br>_Example_: `${white}` will become `${black}` in dark mode.|
|**IGNORE INLINE STYLE**|Prevents inline style analysis of matched elements.|_Example_: `<p style="color: red">` element's style attribute will not be changed.|
|**IGNORE IMAGE ANALYSIS**|Prevents background images from being analyzed for matched selectors.|

## Issues 
- [[@Dark Reader Not Inverting Colors in Bing Chat]]