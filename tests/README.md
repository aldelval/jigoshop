[Jigoshop](http://jigoshop.com) Testing Suite [Jigoshop](http://jigoshop.com)  [![Build Status](https://secure.travis-ci.org/jigoshop/jigoshop.png?branch=dev)](http://travis-ci.org/jigoshop/jigoshop)
=================

This test-suite uses PHPUnit to ensure Jigoshop's code quality.

Travis-CI Automated Testing
-----------

The dev branch of Jigoshop is automatically tested on Travis-ci.org. 
Click on the image above to see the latest test's output.
Travis-CI will also automatically test all new pull requests to make sure they will not break our build.


Quick start (for manual runs)
-----------------------------

Clone the repo.

    git clone git://github.com/jigoshop/jigoshop.git

    cd jigoshop
    # init submodules to grab wordpress test helper
    git submodule init && git submodule update


Copy & edit wordpress test environment file

    cp vendor/wordpress-tests/unittests-config-sample.php vendor/wordpress-tests/unittests-config.php

Now edit unittests-config.php in your favorite editor. Make sure to have an empty database ready(all data will die) and
that your path to wordpress is correct.

Jigoshop does not need to be in the wp/plugins dir. For example in travis-ci().travis.yml we copy wordpress into vendor/wordpress

    <?php
    /* Path to the WordPress codebase you'd like to test. Add a backslash in the end. */
    define( 'ABSPATH', 'path-to-WP/' );

    define( 'DB_NAME', 'jigoshop_test' );
    define( 'DB_USER', 'user' );
    define( 'DB_PASSWORD', 'password' );

    # .. more you probably don't need to edit


Run the test from jiigoshop plugin root folder

    phpunit


Install phpunit on Ubuntu
-------------------------

In case your are using ubuntu(12+), install phpunit like this:

    sudo apt-get install pear
    sudo pear config-set auto_discover 1
    sudo pear install pear.phpunit.de/PHPUnit
	
##Install phpunit on Windows
--------------------------
###Step 1A: Install PEAR (if your localhost **does not** come with it)
Easiest way is to install PEAR is to download go-pear.phar.
Put it in your PHP bin folder.
Then open CMD (make sure you right click run as admin, **even** if you are admin) and run:

	php -d phar.require_hash=0 PEAR/go-pear.phar

For prompts:
Enter, Enter, Enter, Enter

Then open a new CMD and type in

	pear

Should produce output.

###Step 1B: Install PEAR (if your localhost **does** come with it)
Depending on your OS distribution and/or your PHP environment, you may need to install 
PEAR or update your existing PEAR installation before you can proceed with the instructions
in this section.

	pear upgrade PEAR

Above usually suffices to upgrade an existing PEAR installation. 
The PEAR Manual explains how to perform a fresh installation of PEAR.

### Step 2: Install PHPUnit by doing:

	pear config-set auto_discover 1
	pear install --force --alldeps pear.phpunit.de/PHPUnit
	