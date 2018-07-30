# WordPress Debugging

* Contributors: [Andy Fragen](https://github.com/afragen)
* Tags: debug, support
* Requires at least: 4.6
* Requires PHP: 5.6
* Tested up to: 5.0
* Stable tag: master
* Donate link: <http://thefragens.com/github-updater-donate>
* License: MIT

A debugging/support plugin for WordPress.

## Description

This plugin sets the following debug constants in `wp-config.php` on plugin activation and removes them on plugin deactivation. Debug constants per [WordPress Debugging Tools](https://tommcfarlin.com/native-wordpress-debugging-tools/) by Tom McFarlin.

```php
define( 'WP_DEBUG', true );
define( 'WP_DEBUG_LOG', true );
define( 'WP_DEBUG_DISPLAY', true );
@ini_set( 'display_errors', 1 );
define( 'SCRIPT_DEBUG', true );
define( 'SAVEQUERIES', true );
```

[Query Monitor](https://wordpress.org/plugins/query-monitor/) and [Debug Quick Look](https://github.com/norcross/debug-quick-look) plugins are installed and activated as dependencies to aid in debugging and troubleshooting.

[Debug Bar](https://wordpress.org/plugins/debug-bar/) plugin is an optional dependency.

[GitHub Updater](https://github.com/afragen/github-updater) plugin is optional dependency for plugin updates.

You may use the filter `wp_debugging_constants` to add or remove your own constants. You **must** return an array of defined constants.

```php
add_filter( 'wp_debugging_constants',
    function( $constants ) {
        $more_constants = array(
            "define( 'MY_ADDITIONAL_CONSTANT','12356' );"
        );
        return array_merge($constants, $more_constants);
    }
);
```

## Development

PRs are welcome against the `develop` branch.
