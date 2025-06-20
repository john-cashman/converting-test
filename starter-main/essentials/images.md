---
title: Images and Embeds
description: Add image, video, and other HTML elements
icon: image
---

# Images

![](https://mintlify-assets.b-cdn.net/bigbend.jpg)

### Image

#### Using Markdown

The [markdown syntax](https://www.markdownguide.org/basic-syntax/#images) lets you add images using the following code

```md
<figure><img src="/path/image.jpg" alt="title"><figcaption></figcaption></figure>
```

Note that the image file size must be less than 5MB. Otherwise, we recommend hosting on a service like [Cloudinary](https://cloudinary.com/) or [S3](https://aws.amazon.com/s3/). You can then use that URL and embed.

#### Using Embeds

To get more customizability with images, you can also use [embeds](../../writing-content/embed.md) to add images

```html
<img height="200" src="/path/image.jpg" />
```

### Embeds and HTML elements

\


Mintlify supports [HTML tags in Markdown](https://www.markdownguide.org/basic-syntax/#html). This is helpful if you prefer HTML tags to Markdown syntax, and lets you create documentation with infinite flexibility.

#### iFrames

Loads another HTML page within the document. Most commonly used for embedding videos.

```html
<iframe src="https://www.youtube.com/embed/4KzFe50RQkQ"> </iframe>
```
