
- from [[@Dark Reader Not Inverting Colors in Bing Chat]] 
- improving [[$Solution 1 - Dark Reader Issue]]
---
- Summary of improvements : 
	- The main search "card" is now inverted properly ![[Solution 2.jpg]]
	- The chat interface is now inverted properly ![[Solution 2 - 1.jpg]]

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


- Problems
	- Not a _dynamic_ solution to the issue 

