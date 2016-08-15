# Multi-res resources

## Abstract
The multi-res resource feature allows the developer to load a low-res, lightweight placeholder for some resource so the user experience is not interrupted by long loading resources.

## Proposed Usage

### Markup
```html
<img src="~/some-img-lowRes.jpg" multi-res-resource="{url:'~/some-img-highRes.png',type:'image'}">
```  

## Options

### **url** - *required*, string
The **url** is the location where the lazy loaded multi-res resource can be found.
<hr>

### **type** - *required*, string
```image```
<hr>

### **loader** - *optional*, boolean, ```default = false```
When true, the **loader** option provides visual feedback that something is happening to the resource.
