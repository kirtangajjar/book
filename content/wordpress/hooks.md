# WordPress Hooks

## What are Hooks ?

WordPress action and filter hooks are what makes WordPress incredibly extendable. These hooks are very easy to use if someone else has already wrote them, and you just had to hook something in.

## The Difference Between Actions and Filters

The main difference between actions and filters is the purpose they are used for and how they are declared and used. Here’s a quick summary.

#### - Actions

* When something has to be added
* declared with `add_action()`.
* used with `do_action()`.

### - Filters

* When something has to be changed
* declared with `apply_filters()`.
* used with `add_filters()`.

## Examples

You can create a wordpress action with the following code.

```
<?php 
add_action( 'my_action_hook_name', 'my_action_function_name', $priority );

function my_action_function_name() {
  // things your function should do
}
// Note: $priority is optional, and defaults to 10
?>
```

Multiple functions to a single action hook, allowing many possibities of adding functionality to a particular area.  
When the above code is executed, WordPress searches the actions list for '`my_action_hook_name`'. If `my_action_hook_name` is not found, WordPress creates the action hook.

If `my_action_hook_name` is already declared, WordPress tries to find out when it should execute the function with the $priority . The lower a number given to priority, the earlier that particular code will execute.

Since you now know how to create an WordPress action, the next step is to know how to use it.

## Using WordPress Actions

You can you the wordpress action with the following code.

```
<?php 
do_action( 'my_action_hook_name' ); 
?>
```

When the action is called, all functions that are ‘hooked’ to this action will get executed.

From what I see, action hooks are usually used to output information or do some additional logic.

## Declaring WordPress Filters

WordPress filters are more difficult to understand compared to actions.

Lets first talk about how to declare filters first, followed by understanding how to modify the information used by filters.

Filters are declared with the `apply_filters()` function shown below.

```
<?php 
$output = apply_filters( 'filter_name', 'filter_args' ); 
?>
```

In the code mentioned above, the declared filter has a name of `filter_name` with default value '`filter_args`'. filter arguments can be strings or even arrays if you like them to.

## Changing the passed value to filter hooks

To change the value of $output, you have to pass the value through a filter function.

```
<?php 
add_filter( 'filter_name', 'my_filter_function' ); 

function my_filter_function ( $args ) {
    $args = 'my new value'; 
    return $args;
}
?>
```

In this case, `$args`, which currently contains `array('one','two')` is the default value passed to `$output`. For the code above, I have changed $args to `my_new_value`, which will be passed on to $output when the filter function executes. The value of `$output` is now `my_new_value`

following are some more filter and action function with refrence URL

## Filter Functions

* [has\_filter\(\)](https://developer.wordpress.org/reference/functions/has_filter/)
* [add\_filter\(\)](https://developer.wordpress.org/reference/functions/add_filter/)
* [apply\_filters\(\)](https://developer.wordpress.org/reference/functions/apply_filters/)
* [apply\_filters\_ref\_array\(\)](https://developer.wordpress.org/reference/functions/apply_filters_ref_array/)
* [current\_filter\(\)](https://developer.wordpress.org/reference/functions/current_filter/)
* [remove\_filter\(\)](https://developer.wordpress.org/reference/functions/remove_filter/)
* [remove\_all\_filters\(\)](https://developer.wordpress.org/reference/functions/remove_all_filters/)
* [doing\_filter\(\)](https://developer.wordpress.org/reference/functions/doing_filter/)

## Action Functions

* [has\_action\(\)](https://developer.wordpress.org/reference/functions/has_action/)
* [add\_action\(\)](https://developer.wordpress.org/reference/functions/add_action/)
* [do\_action\(\)](https://developer.wordpress.org/reference/functions/do_action/)
* [do\_action\_ref\_array\(\)](https://developer.wordpress.org/reference/functions/do_action_ref_array/)
* [did\_action\(\)](https://developer.wordpress.org/reference/functions/did_action/)
* [remove\_action\(\)](https://developer.wordpress.org/reference/functions/remove_action/)
* [remove\_all\_actions\(\)](https://developer.wordpress.org/reference/functions/remove_all_actions/)
* [doing\_action\(\)](https://developer.wordpress.org/reference/functions/doing_action/)

## Activation/Deactivation/Uninstall Functions

* [register\_activation\_hook\(\)](https://developer.wordpress.org/reference/functions/register_activation_hook/)
* [register\_uninstall\_hook\(\)](https://developer.wordpress.org/reference/functions/register_uninstall_hook/)
* [register\_deactivation\_hook\(\)](https://developer.wordpress.org/reference/functions/register_deactivation_hook/)

## References

* [https://developer.wordpress.org/plugins/hooks/](https://developer.wordpress.org/plugins/hooks/)
* WordPress Codex : [http://codex.wordpress.org/Plugin\_API](http://codex.wordpress.org/Plugin_API)
* WordPress Hooks Database : [http://adambrown.info/p/wp\_hooks](http://adambrown.info/p/wp_hooks)
* Otto : [http://ottopress.com/2011/actions-and-filters-are-not-the-same-thing/](http://ottopress.com/2011/actions-and-filters-are-not-the-same-thing/)
* codeTutplus : [http://code.tutsplus.com/articles/the-beginners-guide-to-wordpress-actions-and-filters--wp-27373](http://code.tutsplus.com/articles/the-beginners-guide-to-wordpress-actions-and-filters--wp-27373)



