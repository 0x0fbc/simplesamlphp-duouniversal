simplesamlphp-module-duouniversal
==========================
Two-factor authentication module using Duo Security Universal Prompt for SimpleSAMLphp.

### This module is still in development and is not production-ready, use at your own risk!

# Installation
1. `cd` into the root of your SimpleSAMLphp installation
2. run `composer require "0x0fbc/simplesamlphp-module-duouniversal"`
3. Copy `module_duouniversal.php` from the `config-templates` directory of this repo to the config directory of your SimpleSAMLphp deployment.
4. Create (if you haven't already) a Duo Universal WebSDKv4 application in the "applications" section of your Duo deployment's admin console and set the following values in the `defaultDuoApp` section of the config:
   1. `clientID` to the "Client ID"
   2. `clientSecret` to the "Client Secret"
   3. `apiHost` to the "API hostname"
   4. `usernameAttribute` to the SAML attribute which correlates to usernames in your Duo deployment.
5. Add an entry into your authentication processing filter chain with the following contents:
```php
array(
    'class' => 'duouniversal:DuoUniversal',
),
```

This will enable the module for the IdP/SP of your choice (or globally if you insert it into the authproc chain in the SimpleSAML global config.php).

The Duo application config used by a particular SP can be changed from the default by adding additional named entries to the `alternateDuoApps` section of the config and then mapping SP EntityIDs to application names in `spDuoOverrides`. Duo can be bypassed per-SP by mapping the SP's EntityID to 'bypass' in the same section. See the comments in the `config-templates/module_duouniversal.php` file for examples.

Based on the original Duo Security module by Kevin Nastase, as forked by Scott Carlson.

- https://github.com/knastase/simplesamlphp-duosecurity
- https://github.com/scottcarlson/simplesamlphp-duosecurity
