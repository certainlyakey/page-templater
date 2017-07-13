# WordPress Page Templater

A fork of Page Templater plugin by WPExplorer (http://www.wpexplorer.com/wordpress-page-templates-plugin/). 

This plugin has a little bit different scope than the original one, as it adds virtual page templates to WP admin that do not need a file for each of them to be existing in the plugin/theme. That means that the page templates will probably use a base template (such as `singular.php` or `page.php`).

## Installation

Drop the plugin into your plugins folder, use the hook to add templates' filenames and names (no actual files need to be created, but filenames will serve as ids).

## Hooks

Use `pagetemplater_change_custom_templates_list` filter to add new templates from a theme:

````
function pagetemplater_return_custom_templates($plugin_templates) {
  $theme_templates = array( 
    'good.php' => 'It\'s Good to Be Bad',
    'heybabe.php' => 'Hey babe',
  );
  $custom_templates = array_merge($plugin_templates, $theme_templates);
  return $custom_templates;
}

add_filter( 'pagetemplater_change_custom_templates_list', 'pagetemplater_return_custom_templates' );
````
