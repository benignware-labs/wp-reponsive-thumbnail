wp-responsive-thumbnail
=======================

> Responsive thumbnails per breakpoints  (Beta)

This plugin lets theme developers configure media breakpoints for different images sizes.
It works by wrapping the image inside a picture tag and providing the appropriate source elements.

## Usage

Add custom image sizes

```php
add_image_size( 'large_wide', 1440, 560, true );
add_image_size( 'large_wide_medium', 768, 360, true );
add_image_size( 'large_wide_small', 480, 480, true );
```

Configure image-sizes at certain breakpoints by using the `add_responsive_thumbnail`-method:

```php
if (function_exists('add_responsive_thumbnail')) {
  add_responsive_thumbnail('large_wide', array(
    480 => 'large_wide_small',
    768 => 'large_wide_medium'
  ));
}
```

Call `the_post_thumbnail` as usual:

```
the_post_thumbnail('large_wide');
```

The generated output looks like this:

```html
<picture>
  <source media="(max-width: 480px)" srcset="http://127.0.0.1:9090/wp-content/uploads/2016/04/image-480x480.jpg 480w"/>
  <source media="(max-width: 768px)" srcset="http://127.0.0.1:9090/wp-content/uploads/2016/04/image-768x360.jpg 768w"/>
  <img class="attachment-large_wide size-large_wide wp-post-image" alt="image" src="http://127.0.0.1:9090/wp-content/uploads/2016/04/image-1440x560.jpg">
</picture>
```