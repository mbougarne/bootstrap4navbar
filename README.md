# Bootstrap 4 Navbar menu for WordPress
This is a walker class for **Bootstrap 4** that extends the WordPress _**Walker_Nav_Menu**_  to use it within your theme.
## Note
You must include the bootstrap javascript file to make the mobile version of the menu with the dropdown working
## Set Up
Move the _**walker-bootstrab-nav-menu.php**_ file to your theme-folder, then add it to your  _**functions.php**_ :
```php
  # Add extended WordPress menu walker
  require_once('walker-bootstrab-nav-menu.php');
```
## How to use it?
>Add this under the **Bootstrap** navbar-toggler button
```php
<?php
   wp_nav_menu([
     'theme_location'  => 'theme-location', // That you defined in functions.php (register_nav_menus)
     'container'       => 'div',
     'container_id'    => 'containerId', // It must be the same as in button data-target
     'container_class' => 'collapse navbar-collapse',
     'menu_id'         => false, // You can add an Id to the <ul> If you need
     'menu_class'      => 'navbar-nav',
     'fallback_cb'     => false,
     'walker'          => new Walker_Bootstrab_Nav_Menu()
   ]);
?>
```
> Here is a full example
```php
<nav class="navbar navbar-expand-lg navbar-light bg-light">
  <a class="navbar-brand" href="#">Navbar</a>
  <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#booMenu" 
  aria-controls="booMenu"  aria-expanded="false" aria-label="Toggle navigation">
    <span class="navbar-toggler-icon"></span>
  </button>
  <?php
     wp_nav_menu([
       'theme_location'  => 'primary',
       'container'       => 'div',
       'container_id'    => 'booMenu',
       'container_class' => 'collapse navbar-collapse',
       'menu_id'         => 'mainMenu',
       'menu_class'      => 'navbar-nav',
       'fallback_cb'     => false,
       'walker'          => new Walker_Bootstrab_Nav_Menu()
     ]);
  ?>
</nav>
```
