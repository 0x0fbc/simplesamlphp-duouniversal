simplesamlphp-duouniversal
==========================
Two-factor authentication module using Duo Security Universal Prompt for SimpleSAMLphp.
Nowhere near production-ready.

Based on original Duo Security module by Kevin Nastase, forked by Scott Carlson.

- https://github.com/knastase/simplesamlphp-duosecurity
- https://github.com/scottcarlson/simplesamlphp-duosecurity

-----
OLD README: simplesamlphp-duosecurity
=========================

Two factor authentication module using Duo Security for SimpleSAMLphp

Usage:
Rename the folder to duosecurity and place in your SimpleSAMLphp modules folder

Set up a Web SDK integration on your Duo admin website.
see https://www.duosecurity.com/docs/duoweb for more information

In config/config.php, activate the Duo Security module by adding it to the
authentication filters section. (under 'authproc.idp')

            80 => array(

                'class' => 'duosecurity:Duosecurity',
            
                'akey' => 'SECRET KEY UNIQUE TO YOUR APP MUST BE 40 CHARACTERS',
            
                // The following values can be found on your Duo admin page
            
                'ikey' => '',
            
                'skey' => '',
            
                'host' => '',

                // Specify the attribute to be used as the Duo username

                'usernameAttribute' => '',

            ),

Do not change the names of any files in the module
