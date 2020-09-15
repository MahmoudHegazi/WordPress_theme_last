# WordPress_theme_last
From Scratch, using udemy course


### Example in posts
*  in the case1 wordpress will look for file content-excerpt.php if it not found it will do nothing.
```php
//case1
get_template_part( 'partials/post/content-excerpt');
```
*  in the case2 it will look for content-excerpt.php if not found it will look for content.php so the second case is good if u have multipale template.
```php //case2
get_template_part( 'partials/post/content', 'excerpt');
```
#### walker class work only with nested menu not the main menu 
######  absoulte min require to create theme is index.php and style.css << we add the theme name in style.css
######  jquery is installed by wordpress we need only eneque it's script 
```php
wp_enqueue_script( 'jquery' )
```

// if you need to modify tags and data before use (use filter hod)
```php 
add_filter( 'the_title', 'ju_title' );
```
// if you need perform custom action so use  action hooks
```php
add_action( 'wp_footer', 'ju_footer_shoutout' );
```


### top note

* how to add ajax in wordpress customizer?

1. we need to use add setting define the setting, (add it to database)
2. then we going to add controller with this setting, and we edit the php if statment in the place we going to have changes
3. we need jquery and add this action 
```php
add_action( 'customize_preview_init', 'ju_customize_preview_init' );
```
4. define this hock to allow ajax .
```php
function ju_customize_preview_init() {
  wp_enqueue_script(
      'ju_theme_customizer',
      get_theme_file_uri( '/assets/js/theme-customize.js' ),
      [ 'jquery', 'customize-preview' ],
      false,
      true
  );
}

```
5.  we have now ever thing ready, sometimes cash may make things not work clear cashe or try another browser.


```php 
// load the post thumbnail inside the loop
<?php the_post_thumbnail(); ?>

```
