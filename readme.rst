Keyring
=======

Contributors: beaulebens, mdawaffe, jshreve, jkudish, automattic  
Tags: authentication, security, oauth, http basic, authorization, facebook, foursquare, instagram, twitter, google  
Requires at least: 4.0  
Tested up to: 6.2  
Stable Tag: 3.0  

An authentication framework that handles authorization/communication with most popular web services.

Description
-----------

**See the `Keyring Developer's Guide <https://beaulebens.com/projects/wp-keyring/>`_ for more details.**

Keyring provides a very hookable, completely customizable framework for connecting your WordPress to an external service. It takes care of all the heavy lifting when making authenticated requests, so all you need to do is implement cool features and not worry about these tricky bits.

Out of the box, Keyring currently comes with base Service definitions for:

- HTTP Basic,
- OAuth1, and
- OAuth2.

And includes ready-to-use definitions for:

- `500px <https://500px.com/>`_
- `Eventbrite <https://eventbrite.com/>`_
- `Facebook <https://facebook.com/>`_
- `Fitbit <https://fitbit.com/>`_
- `Flickr <https://flickr.com/>`_
- `Foursquare <https://foursquare.com/>`_
- `Google Analytics <https://www.google.com/analytics/>`_
- `Google Contacts <https://www.google.com/contacts/>`_
- `Google Mail <https://www.google.com/mail/>`_
- `Instagram <https://instagram.com/>`_
- `Instapaper <https://instapaper.com/>`_
- `Jetpack <https://jetpack.com/>`_/`WordPress.com <https://wordpress.com/>`_
- `LinkedIn <https://linkedin.com/>`_
- `Nest <https://nest.com/>`_
- `Pinterest <https://pinterest.com/>`_
- `RunKeeper <https://runkeeper.com/>`_
- `Strava <https://strava.com/>`_
- `TripIt <https://tripit.com/>`_
- `Tumblr <https://tumblr.com/>`_
- `Twitter <https://twitter.com/>`_
- `Yahoo! Updates <https://yahoo.com/>`_
- `YouTube <https://youtube.com/>`_

You can very easily write your own Service definitions and then use all the power of Keyring to hook into that authentication flow. See the `Keyring Developer's Guide <https://beaulebens.com/projects/wp-keyring/>`_ for more details.

Contributions are welcome via `GitHub pull request <https://github.com/beaulebens/keyring>`_.

Installation
------------

1. Install Keyring either via the WordPress.org plugin directory, or by uploading the files to your server.
2. Activate Keyring in Plugins > Installed Plugins.
3. Go to Tools > Keyring > Add New and you will be prompted to configure services before making user-specific connections to them.

Frequently Asked Questions
--------------------------

How Do I Use Keyring in my Plugin?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Check out the `Keyring Developer's Guide <https://beaulebens.com/projects/wp-keyring/>`_.

See `Keyring Social Importers <http://wordpress.org/plugins/keyring-social-importers/>`_ for an example. You can also extend Keyring Service classes directly, rather than attaching the service as a property to an object (like the Importers do).

Will Keyring Work on My WordPress?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Keyring **requires PHP 5.3+ to work**, because it makes use of some modern features in PHP like late static binding and abstract classes. Other than that, as long as you meet the minimum required WP version, you should be OK to get started. If you get a cryptic "T_PAAMAYIM_NEKUDOTAYIM" error, you need to upgrade to PHP 5.3+. If you get an error about "Parse error: syntax error, unexpected T_FUNCTION in .../wp-content/plugins/keyring/keyring.php on line 50" you also need to upgrade PHP.

Your webserver will also need to be able to make outbound HTTPS requests for some operations with some services to work correctly.

How Do I Configure Services?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Most services within Keyring require some sort of API key/secret before you can connect to them.

1. Go to Tools > Keyring > Add New.
2. Click the name of a service in the bottom section, or 'Manage' next to one of the services in the top section.
3. Enter your API details (you will need to get those from the specific service; most config screens provide links/details on how to set them up).
4. Click 'Save Changes'.
5. Now you should be able to create a new connection to that service from the "Add New" screen.

How Do I Connect to 'x' Service?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Go to Tools > Keyring > Add New.
2. Click the name of the service in the top section (if it's in the bottom section, then that service has not been configured for API access yet, see above).
3. Follow through any authentication prompts to connect.
4. You should now be connected, and your connection details should be listed on the Keyring admin page (which you will be redirected to once authentication is complete).

Now What?
^^^^^^^^^

Keyring just provides a framework for handling connections to external services. You need to download another plugin which makes use of Keyring to do anything useful (e.g., an importer or content-syncing plugin).

How Does Keyring Store Tokens?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

- By default, on a single-site install, Keyring stores tokens in your wp_posts table with a custom post type of 'keyring_token'.
- On a multi-site install, Keyring will store tokens in a specified blog/site's wp_posts (so you can set a single site aside for just token storage if you like).
- Keyring provides a framework for you to write your own token storage engine (see store.php and includes/stores/).

How Do I Add to the List of Services Keyring Can Connect To?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Add files to includes/services/extended/ that either implement one of the includes/services/core/ service foundations or start from scratch. Follow one of the existing service definitions for a template, and see service.php in the root of Keyring for some detail on methods you need to define, and optional ones that might make your life easier.

Changelog
---------

For a detailed changelog, refer to the source repository or plugin details.
