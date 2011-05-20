=== Boone's Sortable Columns  ===
Contributors: boonebgorges
Tags: columns, tables, custom post types
Requires at least: WordPress 3.1
Tested up to: WordPress 3.2-beta
Stable tag: 1.0

A handy, extensible class for adding sortable columns your custom post type lists.

== Description ==

Here's how I recommend using the class.

1. Either activate this plugin, or include the class in your own plugin file.
1. When you start to render the page with the post list, instantiate the pagination class:
`$pagination = new BBG_CPT_Pag;`
1. When constructing your query arguments (for query_posts() or WP_Query), you can use the class to get your pagination arguments out of the $_GET parameters. For instance:
`$args = array(
...
'posts_per_page' => $pagination->get_per_page,
'paged' => $pagination->get_paged
...
);
query_posts( $args );`
1. After firing the query, use the `setup_query()` method to populate the rest of the class. If you used `query_posts()`, you don't need an argument:
`$pagination->setup_query();`
If you use `new WP_Query`, you'll have to pass the query object:
`$my_query = new WP_Query;
$pagination->setup_query( $my_query );`
1. Then you can use all sorts of fun methods, like
`$pagination->paginate_links();
$pagination->currently_viewing_text();`
