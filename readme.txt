=== User-Activity-Monitoring ===
Contributors: amarinediary
Tags: user, activity, monitoring, status
Requires at least: 3.0.0
Tested up to: 5.7.1
Requires PHP: 4.0
Stable tag: 1.0.0
License: CC0 1.0 Universal (CC0 1.0) Public Domain Dedication
License URI: https://github.com/amarinediary/User-Activity-Monitoring/blob/main/LICENSE

A non-invasive, lightweight WordPress plugin adding user activity monitoring support. User-Activity-Monitoring is a plug-and-play plugin with no required configuration.

== Description ==

A non-invasive, lightweight WordPress plugin adding user activity monitoring support. User-Activity-Monitoring is a plug-and-play plugin with no required configuration.

== Get a specific user activity status from it's ID ==

`
<?php 

/**
 * Get a specific user activity status from it's ID.
 *
 * @since 1.0.0
 *
 * @param Integer $user_id The user ID.
 *
 * @return Bool True for online.
 */
$user_activity_monitoring->is_user_currently_online( $user_id );
`

= Example: Display the currently viewed user (`author.php`) activity status =

`
<?php 

if ( get_queried_object() instanceof \WP_User && is_author() ) {

  if ( $user_activity_monitoring->is_user_currently_online( get_queried_object_id() ) ) {

    echo '🟢 Online';

  } else {

    echo '🔴 Offline';

  };

};
`

== Get an array of all users currently online ==

`
<?php 

/**
 * Get an array of all users currently online.
 *
 * @since 1.0.0
 *
 * @return Array An array of currently online users ID.
 */
$user_activity_monitoring->get_currently_online_users();
`

= Example: Display all users currently online =

`
<?php 

$currently_online_users = $user_activity_monitoring->get_currently_online_users(); 

echo '<ul>';

foreach( $currently_online_users as $user_id ) {

  if ( get_current_user_id() !== $user_id ) {

    echo '<li><a href="' . esc_url( get_author_posts_url( $user_id ) ) . '">
      @' . get_userdata( $user_id )->display_name . '🟢 Online
    </a></li>';

  };

};

echo '</ul>';
`

= Example: Display the total count of users currently online =

`
<?php 

$currently_online_users_count = $user_activity_monitoring->get_currently_online_users(); 

echo sizeof( $currently_online_users_count );
`

== Get an array of all users recently offline ==

`
<?php 

/**
 * Get an array of all users recently offline.
 *
 * @since 1.0.0
 *
 * @return Array An array of recently offline users ID.
 */
$user_activity_monitoring->get_recently_offline_users();
`

= Example: Display all users recently offline =

`
<?php 

$recently_offline_users = $user_activity_monitoring->get_recently_offline_users(); 

echo '<ul>';

foreach( $recently_offline_users as $user_id ) {

  if ( get_current_user_id() !== $user_id ) {

    echo '<li><a href="' . esc_url( get_author_posts_url( $user_id ) ) . '">
      @' . get_userdata( $user_id )->display_name . '🔴 Offline
    </a></li>';

  };

};

echo '</ul>';
`

== While in a template-part ==

To be abble to use a method from a template-part, it is required to pass the class variable to that template-part. 

- Source @ [https://developer.wordpress.org/reference/functions/get_template_part/](https://developer.wordpress.org/reference/functions/get_template_part/)

> You can pass additional arguments to a template-part via the `$args` parameter.

`
<?php

get_template_part( 'templates', 'my-awesome-template-part', 
    array( 
        'user_activity_monitoring' => $user_activity_monitoring, 
    ) 
);
`

Then, call the argument from the template-part via `$args['my_argument_handle']`.

`
<?php

$user_activity_monitoring = $args['user_activity_monitoring'];

// ...
`

== Bugs and feature requests ==

A problem ? An idea ? Please [Open a new issue on GitHub](https://github.com/amarinediary/User-Activity-Monitoring/issues/new) or [Ask a question on Wordpress User-Activity-Monitoring support](https://wordpress.org/support/plugin/user-activity-monitoring/#new-topic-0).

== Copyright and license ==

Released under [CC0 1.0 Universal (CC0 1.0) Public Domain Dedication](https://github.com/amarinediary/User-Activity-Monitoring/blob/main/LICENSE).

== Share your experience ==

* [Write us a review](https://wordpress.org/support/plugin/user-activity-monitoring/reviews/#new-post)

★★★★★
> Just what you need it.
> Nothing more, nothing less. - [amarinediary](https://profiles.wordpress.org/amarinediary/)

== Frequently Asked Questions ==

= GitHub Plugin URI =
Visit our GitHub page @ [https://github.com/amarinediary/User-Activity-Monitoring](https://github.com/amarinediary/User-Activity-Monitoring).

== Installation ==

If you have a copy of the plugin as a zip file, you can manually upload it and install it through the Plugins admin screen.

1. Navigate to Plugins `→` Add New.
2. Click the Upload Plugin button at the top of the screen.
3. [Download the plugin as a zip file](https://downloads.wordpress.org/plugin/user-activity-monitoring.zip), Select it from your local filesystem.
4. Click the Install Now button.
5. When installation is complete, you’ll see “Plugin installed successfully.” Click the Activate Plugin button at the bottom of the page.

== Changelog ==

= 1.0.0 =
* Initial release.

== Upgrade Notice ==

= 1.0.0 =
* Initial release.