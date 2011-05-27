=== Boone's Sortable Columns  ===
Contributors: boonebgorges
Tags: columns, tables, custom post types
Requires at least: WordPress 3.1
Tested up to: WordPress 3.2-beta
Donate link: http://teleogistic.net/donate
Stable tag: 1.1

A handy, extensible class for adding sortable columns your custom post type lists.

== Description ==

Here's how I recommend using the class.

1. Either activate this plugin, or include the class in your own plugin file.
2. When you start to render the page with the post list, define some columns and then instantiate the class:
`$cols = array(
	array(
		'name'		=> 'restaurant_name',
		'title'		=> 'Restaurant Name',
		'css_class'	=> 'restaurant-name',
		'is_default'	=> true
	),
	array(
		'name'		=> 'cuisine_type',
		'title'		=> 'Cuisine Type',
		'css_class'	=> 'cuisine-type',
		'default_order' => 'desc'
	)
);
$sortable = new BBG_CPT_Sort( $cols );`
3. As you render your table, you can use all sorts of fun methods to create column headers. Example:
`<table class="widefat">
	<thead>
	<?php if ( $sortable->have_columns() ) : ?>
		<?php while ( $sortable->have_columns() ) : $sortable->the_column() ?>
			<th class="<?php $sortable->the_column_css_class() ?>">
				<a href="<?php $sortable->the_column_next_link( 'url' ) ?>"><?php $sortable->the_column_title() ?></a>
			</th>
		<?php endwhile ?>
	<?php endif ?>
	</thead>
	
	<tbody>
	...
	</tbody>

</table>`

== Installation ==
Two choices:
1. Install from the plugins repository and activate for use in your theme
or 
2. Copy the BBG_CPT_Sort class into your own plugin/theme and require it manually.

== Changelog == 

= 1.1 =
* Adds setup_base_url() method, for greater control over how column header URLs are generated

= 1.0 =
* Initial release
