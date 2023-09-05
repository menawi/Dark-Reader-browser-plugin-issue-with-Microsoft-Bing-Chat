[$$ Best Solution (thus far).md](https://github.com/menawi/Dark-Reader-browser-plugin-issue-with-Microsoft-Bing-Chat/files/12526255/Best.Solution.thus.far.md)[$Solution 2 - Dark Reader Issue.md](https://github.com/menawi/Dark-Reader-browser-plugin-issue-with-Microsoft-Bing-Chat/files/12526249/Solution.2.-.Dark.Reader.Issue.md)[$Solution 1 - Dark Reader Issue.md](https://github.com/menawi/Dark-Reader-browser-plugin-issue-with-Microsoft-Bing-Chat/files/12526241/Solution.1.-.Dark.Reader.Issue.md)# Dark-Reader-browser-plugin-issue-with-Microsoft-Bing-Chat
# Issue: Dark Reader Not Inverting Colors in Bing Chat

## Problem Description
**Issue Link:** [GitHub Issue #11496](https://github.com/darkreader/darkreader/issues/11496)

The Dark Reader plugin I am using in Microsoft Edge is not functioning correctly when applied to Bing Chat. Specifically, the main chat area is experiencing issues with color inversion. Instead of the expected white text on a dark background, the chat text containers have black text on a dark background. It appears that the CSS property responsible for inverting colors is not being applied correctly to these elements. There may be an obstacle preventing the expected color inversion.

## Goal
My objective is to ensure that the colors are inverted correctly in Bing Chat, with white text on a dark background, as intended by the Dark Reader plugin.

## Working Solutions Explored
I have explored the following solutions to address this issue:

## $Solution 1 - Dark Reader Issue

```css
/* -- @menawi additions for Bing Chat --- */
div.main {
filter: invert(1);
}
.entity-image-button{
filter: initial;
}
.main-container{
filter: invert(1);
}
.container{
filter: invert(1);
}
div.content.text-message-content {
filter: initial !important;
  background-color: #a55b00;
}
/* -- end @menawi for Bing Chat --- */
``` 

- This solution involves examining and addressing any potential issues within the Dark Reader extension itself that may be causing the problem in Bing Chat.

### $Solution 2 - Dark Reader Issue
- Similar to Solution 1, this solution focuses on troubleshooting within the Dark Reader extension to identify and resolve any underlying issues affecting Bing Chat.
- from [[@Dark Reader Not Inverting Colors in Bing Chat]] 
- improving [[$Solution 1 - Dark Reader Issue]]
---
- Summary of improvements : 
	- The main search "card" is now inverted properly ![](attachment/e35634bfb99743e109da345a54c84ce6.jpg)
	- The chat interface is now inverted properly ![](attachment/c35200d052cfa8c754011028aebd5977.jpg)

```css
/* -- @menawi additions for Bing Chat --- */
div.main {
filter: invert(1);
}
.entity-image-button{
filter: initial;
}
.main-container{
filter: invert(1);
}
.container{
filter: invert(1);
}
div.content.text-message-content {
filter: initial !important;
  background-color: #a55b00;
}

cib-see-more-container{
filter: invert(1) ; 
}
/* -- end @menawi for Bing Chat --- */
```


### Solution 2 Refactored OR Best Solution and Why it is Better than Other Solutions![[$$ Best Solution (thus far)#^0ce866]]

[Uploading $$ Best
> [!NOTE]
> **Why This Code Is Better**
> 
> You may have come across an alternative solution [here](https://github.com/darkreader/darkreader/issues/10784#issuecomment-1654598152) , which, although effective, may inadvertently invert colors if Bing's dark mode is already active.
> 
> The code provided below, however, offers a superior solution by ensuring that colors are not inverted when Bing's dark mode is already enabled.

^0ce866


```css

/* -- Global Variables -- */
:root {
    --darkreader-text--cib-color-neutral-foreground: ${black} !important;
    --darkreader-text--cib-color-brand-tertiary-foreground: ${white} !important;
    --cib-color-neutral-layer-card: rgba(255, 255, 255, 0.1) !important;
    --cib-color-brand-secondary-background: rgba(255, 255, 255, 0.1) !important;
    --cib-color-brand-secondary-background-hover: rgba(255, 255, 255, 0.2) !important;
    --cib-color-neutral-layer-overlay: rgba(255, 255, 255, .2) !important;
    --cib-color-neutral-foreground: ${black} !important;
    --cib-color-neutral-layer-card-alt: #131516 !important;
    --cib-color-neutral-app-background: #131516 !important;
    --cib-color-neutral-drawer-background: rgba(255, 255, 255, .05) !important;
    --cib-color-neutral-layer-card-disabled: rgba(255, 255, 255, 0.1) !important;
    --cib-color-stealth-secondary-foreground: ${black} !important;
    --cib-color-stealth-secondary-foreground-pressed: ${black} !important;
}

/* -- Box Shadows -- */
.b_searchboxForm,
.b_searchboxForm:hover,
.b_focus .b_searchboxForm,
#sw_as #sa_ul:not(:empty),
cib-typing-indicator ~ .main-container,
cib-see-more-container {
    box-shadow: ${rgba(0, 0, 0, 0.1)} 0px 0px 0px 1px !important;
}

#b_results > li.b_ans.b_topborder, #b_results > li.b_ans.b_topborder.b_tophb.b_topshad {
    box-shadow: ${rgba(13, 13, 13, 0.05)} 0px 0px 0px 1px !important;
}

/* -- Z-Index -- */
.l_ecrd_imcolheader.gradient {
    z-index: 2 !important;
}

/* -- Background Images -- */
#b_content {
    background-image: none !important;
}

/* -- Opacity -- */
cib-background,
cib-background.background {
    opacity: 0 !important;
}

/* -- Background Colors -- */
cib-tooltip,
.attributions > .attribution-item > .background {
    background: var(--darkreader-neutral-background) !important;
}

/* -- Background with Alpha -- */
cib-message[type="text"]:not([serp-slot="right-rail"]),
button.container > .item-content,
button.container > .item-content:before,
.container > .options-list-container,
.container > .options-list-container li.option button:not([selected]):before,
button.container[serp-slot="none"], button.container[serp-slot="right-rail"],
#fbpgbt,
#stop-responding-button,
cib-feedback,
cib-see-more-caintainer {
    background: ${rgba(50, 50, 50, 0.1)} !important;
}

/* -- Text Color -- */
cib-message[type="text"]:not([serp-slot="right-rail"]),
cib-shared > .content > .ac-container > .ac-textBlock {
    color: var(--darkreader-text--cib-color-neutral-foreground) !important;
}

/* -- Hover Background -- */
button.container[serp-slot="right-rail"]:hover {
    background: ${rgba(0, 0, 0, 0.3)} !important;
}

/* -- Border Color -- */
button.container[serp-slot="none"] {
    border: 1px solid var(--cib-color-brand-secondary-stroke) !important;
}

/* -- Color and Background -- */
.attribution-container > .attribution-items > .attribution-item,
.attribution-container > .attribution-items > button.expand-button,
.ac-container.ac-adaptiveCard > .ac-textBlock > p > .tooltip-target + a > sup {
    color: #A2B7F4 !important;
    background: #050F2E !important;
}

/* -- Background Color -- */
cib-typing-indicator ~ .main-container,
cib-see-more-container {
    background: var(--darkreader-neutral-background) !important;
}

/* -- Icon Opacity -- */
div.icon > svg > g:nth-child(1) > path:nth-child(1) {
    opacity: 0 !important;
}

/* -- Tooltip Background and Text Colors -- */
.ac-container.ac-adaptiveCard > .ac-textBlock > p > .tooltip-target.hover {
    background: var(--cib-color-stealth-primary-foreground-hover) !important;
    color: var(--cib-color-brand-text-highlight-background) !important;
    text-decoration-color: var(--cib-color-brand-text-highlight-background) !important;
}

/* -- Code Block Background -- */
.ac-container.ac-adaptiveCard > .ac-textBlock > p code {
    background: rgba(255, 255, 255, 0.2) !important;
}

/* -- SVG Icon Fill -- */
.container > button:hover > svg-icon {
    fill: var(--cib-color-neutral-primary-background) !important;
}

/* -- Text Color -- */
.content > .ac-container {
    color: var(--darkreader-neutral-text);
}

/* -- Background Image -- */
#b_results .b_algo.b_deeplinks_bg_color_kc {
    background-image: none !important;
}

/* -- Custom Styling for Bing Chat -- */
/* @menawi additions for Bing Chat */
div.main {
    filter: invert(1);
}

.entity-image-button {
    filter: initial;
}

.main-container {
    filter: invert(1);
}

.container {
    filter: invert(1);
}

div.content.text-message-content {
    filter: initial !important;
    background-color: #a55b00;
}

cib-see-more-container {
    filter: invert(1);
}
/* end @menawi for Bing Chat */

/* -- Ignore Inline Style for Specific Elements -- */
IGNORE INLINE STYLE
.b_header_bg
.sp-tpwebicons.WIKI *

``` 



### Card View

![Best Solution - The Card](https://github.com/menawi/Dark-Reader-browser-plugin-issue-with-Microsoft-Bing-Chat/assets/105254409/405c11d3-ee96-4a16-b7e7-8fa284919daa)


### Chat View

![Best Solution - Chat](https://github.com/menawi/Dark-Reader-browser-plugin-issue-with-Microsoft-Bing-Chat/assets/105254409/4e9fe73d-f095-4ff8-a3d3-98db45cf7d88)


## Additional Resources
For more information on how to resolve incorrect color inversions and related issues, you can refer to the [@Dark Reader Documentation](https://github.com/darkreader/darkreader) or related discussions.


> 🟩 Success 
> [[$$ Best Solution (thus far)]] is the most stable so far and I am happy with it.

## Related Keywords
- CSS filter property
- mix-blend-mode
- Linked mentions

