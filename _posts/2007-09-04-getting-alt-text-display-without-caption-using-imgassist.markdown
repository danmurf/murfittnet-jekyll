---
layout: post
title:  "Getting alt text to display without a caption using img_assist"
date:   2007-09-04 21:58:00 +0000
tags: [ Web Development, Web Design, Drupal, Drupal Modules ]
permalink: blog/getting-alt-text-display-without-caption-using-imgassist
---
I ran into a spot of trouble recently with img_assist, in that it only displayed alt text if there was also a caption below the image. Img_Assist takes the alt text from a combination of the title and description, and these fields are filled by default from the title and body of the image node. Although there is no real need for a caption below each image, you will almost always need alt text.

The problem was that Drupal wasn't wrapping the caption in a span, which meant no easy way of hiding it without digging into the module code. This is the HTML output:

```html
<img class="image _original" width="200" height="75" title="Sunset" alt="Sunset" src="http://example.com/files/images/sunset.jpg"/>
<strong>Sunset</strong>
```

It turns out that the HTML filter was set to a lower weight than the inline images filter, so the span was being removed when the page was being processed. To fix this, simply set the HTML filter to something lighter (I set mine to -10) and you'll find the caption is now wrapped in a span. This setting is found in Administer > Site Configuration > Input Formats > Configure Filtered HTML (Or whatever filter you're using) > Rearrange tab. Now you should find that the page displays the caption to accompany the alt text, like this:

```html
<span class="inline none">
<img class="image _original" width="200" height="75" title="Sunset" alt="Sunset"  src="http://example.com/files/images/sunset.jpg"/>
<span class="caption" style="width: 200px;">
<strong>Sunset</strong>
</span>
</span> 
```

Then, to remove the caption from displaying on the screen, use the following CSS:

```css
span.caption {
display:none;
}
```
I think it's a good idea to run the HTML filter first in general so it cleans the unwanted code up but doesn't also interfere with other filters.

Please feel free to post any comments below.