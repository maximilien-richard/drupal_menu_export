Menu Export
==================

Drupal 7 module to export menus easily. Also provides an import function.

Menu Export generates a piece of PHP code which you can store, for example inside a simple .inc file provided by your module. This module also provides an interface to import any of this piece of php code . This module is fully inspired by view and panel export features.

Features
-----------

* Export menu tab.
* Import menu tab.
* Import function to use inside your own code.

Similar modules
-----------

* Menu Import : The main difference beetwen Menu export and Menu Export/Import is the kind of exported data . Menu Export provide an object structure which helps to import more efficiently, thus a simple cut-and-paste is enough to regenerate to menu. It is also possible to store the data provided inside a file and call the `menu_export_menu_import()` function inside you `hook_install` (for example). Menu export aims to provide a structure close to export features provided by ctools or view.
 

We would recommend you to use Menu Export if you need something to deploy faster your project. Nethertheless you should probably have a look to Menu Export/Import if you need something readable and understandable by non-tech person.

Possible improvements
-----------

Create a way to be able to revert any changes on a menu, something like the revert feature provided by view.
Make this module compatible with drush :
* drush menu-import
* drush menu-export
* drush menu revert
* and so forth ...

Requirements
-----------

Drupal 7 (with the core module "Menu" enabled)

Known issues
-----------

No conflicts, no incompatibilities or bug known so far.

Export menu
-----------

1. Go to admin/structure/menu
2. Choose your menu to export (edit menu)
3. Click on "Export Menu" tab
4. Copy / Paste the code into a file
 
Import menu
-----------

An export file generated by this module creates an object `$menu`.

You can import this object with the function `menu_export_menu_import($menu)`

Example of awesome import
-------------------------

```php
  $filepath = drupal_get_path('module', 'my_module') . '/menus';
  $files = drupal_system_listing('/\.inc$/', $filepath, 'name', 0);

  foreach($files as $file) {
    include_once $filepath . "/" . $file->filename;
    menu_export_menu_import($menu);
  }
```

With that piece of code you will be able to import a bunch of menus : just
put some **.inc** files into a directory called **menus** inside your
module **my_module**.

![That's All Falks !](http://goo.gl/EOidtZ)
