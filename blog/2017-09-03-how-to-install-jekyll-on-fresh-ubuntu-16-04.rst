How to install Jekyll on fresh Ubuntu 16.04 LTS
===============================================
.. warning::
	Created on September 03, 2017 and has not been updated yet.

.. note::
	This is a self note blog post and it doesn't contain detailed explanations as in tutorial posts.


As you may notice currently I am using Jekyll for this website more than one year and I am still happy with this decision. In this post, I write the steps that I followed to build this website using **Jekyll 3.5.2** on a fresh install of **Ubuntu 16.04**. You may follow the steps but don't expect a tutorial post.

I use a very basic script named ``build_and_test_before_upload.sh`` to build my website locally:

.. code-block:: none

	#!/usr/bin/env bash
	set -e # halt script on error

	cd ..

	bundle exec jekyll serve --config _config.yml --verbose


Let's try to run script first.

.. code-block:: none

	$ ./build_and_test_before_upload.sh 
	./build_and_test_before_upload.sh: line 6: bundle: command not found

I got an error as expected.

.. code-block:: none

	$ sudo apt-get install ruby ruby-dev make gcc
	$ sudo gem install jekyll bundler

Try it again.

.. code-block:: none

	$ ./build_and_test_before_upload.sh 
	Could not find i18n-0.7.0 in any of the sources
	Run `bundle install` to install missing gems.

There is a missing dependency, let's check it.

.. code-block:: none

	$ gem list

	*** LOCAL GEMS ***

	addressable (2.5.2)
	bigdecimal (1.2.8)
	bundler (1.15.4)
	colorator (1.1.0)
	did_you_mean (1.0.0)
	ffi (1.9.18)
	forwardable-extended (2.6.0)
	io-console (0.4.5)
	jekyll (3.5.2)
	jekyll-sass-converter (1.5.0)
	jekyll-watch (1.5.0)
	json (1.8.3)
	kramdown (1.14.0)
	liquid (4.0.0)
	listen (3.0.8)
	mercenary (0.3.6)
	minitest (5.8.4)
	net-telnet (0.1.1)
	pathutil (0.14.0)
	power_assert (0.2.7)
	psych (2.0.17)
	public_suffix (3.0.0)
	rake (10.5.0)
	rb-fsevent (0.10.2)
	rb-inotify (0.9.10)
	rdoc (4.2.1)
	rouge (1.11.1)
	safe_yaml (1.0.4)
	sass (3.5.1)
	sass-listen (4.0.0)
	test-unit (3.1.7)

Install the missing one.

.. code-block:: none

	$ sudo gem install i18n
	Fetching: i18n-0.8.6.gem (100%)
	Successfully installed i18n-0.8.6
	Parsing documentation for i18n-0.8.6
	Installing ri documentation for i18n-0.8.6
	Done installing documentation for i18n after 0 seconds
	1 gem installed

Check it again, it is on the list now.

.. code-block:: none

	$ gem list

	*** LOCAL GEMS ***

	addressable (2.5.2)
	bigdecimal (1.2.8)
	bundler (1.15.4)
	colorator (1.1.0)
	did_you_mean (1.0.0)
	ffi (1.9.18)
	forwardable-extended (2.6.0)
	i18n (0.8.6)
	io-console (0.4.5)
	jekyll (3.5.2)
	jekyll-sass-converter (1.5.0)
	jekyll-watch (1.5.0)
	json (1.8.3)
	kramdown (1.14.0)
	liquid (4.0.0)
	listen (3.0.8)
	mercenary (0.3.6)
	minitest (5.8.4)
	net-telnet (0.1.1)
	pathutil (0.14.0)
	power_assert (0.2.7)
	psych (2.0.17)
	public_suffix (3.0.0)
	rake (10.5.0)
	rb-fsevent (0.10.2)
	rb-inotify (0.9.10)
	rdoc (4.2.1)
	rouge (1.11.1)
	safe_yaml (1.0.4)
	sass (3.5.1)
	sass-listen (4.0.0)
	test-unit (3.1.7)

Retry.

.. code-block:: none

	$ ./build_and_test_before_upload.sh 
	Could not find i18n-0.7.0 in any of the sources
	Run `bundle install` to install missing gems.

Let's install the correct version.

.. code-block:: none

	$ sudo gem install i18n --version 0.7
	Fetching: i18n-0.7.0.gem (100%)
	Successfully installed i18n-0.7.0
	Parsing documentation for i18n-0.7.0
	Installing ri documentation for i18n-0.7.0
	Done installing documentation for i18n after 0 seconds
	1 gem installed

Let's see the list.

.. code-block:: none

	$ gem list

	*** LOCAL GEMS ***

	addressable (2.5.2)
	bigdecimal (1.2.8)
	bundler (1.15.4)
	colorator (1.1.0)
	did_you_mean (1.0.0)
	ffi (1.9.18)
	forwardable-extended (2.6.0)
	i18n (0.8.6, 0.7.0)
	io-console (0.4.5)
	jekyll (3.5.2)
	jekyll-sass-converter (1.5.0)
	jekyll-watch (1.5.0)
	json (1.8.3)
	kramdown (1.14.0)
	liquid (4.0.0)
	listen (3.0.8)
	mercenary (0.3.6)
	minitest (5.8.4)
	net-telnet (0.1.1)
	pathutil (0.14.0)
	power_assert (0.2.7)
	psych (2.0.17)
	public_suffix (3.0.0)
	rake (10.5.0)
	rb-fsevent (0.10.2)
	rb-inotify (0.9.10)
	rdoc (4.2.1)
	rouge (1.11.1)
	safe_yaml (1.0.4)
	sass (3.5.1)
	sass-listen (4.0.0)
	test-unit (3.1.7)

OK, the correct version is available now. Let's try it again.

.. code-block:: none

	$ ./build_and_test_before_upload.sh
	Could not find minitest-5.9.0 in any of the sources
	Run `bundle install` to install missing gems.

There is another missing dependency.

.. code-block:: none

	$ sudo gem install minitest --version 5.9.0
	Fetching: minitest-5.9.0.gem (100%)
	Successfully installed minitest-5.9.0
	Parsing documentation for minitest-5.9.0
	Installing ri documentation for minitest-5.9.0
	Done installing documentation for minitest after 0 seconds
	1 gem installed

Now, retry.

.. code-block:: none
	
	$ ./build_and_test_before_upload.sh
	Could not find thread_safe-0.3.5 in any of the sources
	Run `bundle install` to install missing gems.

Oh, no! Dependencies aren't complete yet.

.. code-block:: none

	$ sudo gem install thread_safe --version 0.3.5
	Fetching: thread_safe-0.3.5.gem (100%)
	Successfully installed thread_safe-0.3.5
	Parsing documentation for thread_safe-0.3.5
	Installing ri documentation for thread_safe-0.3.5
	Done installing documentation for thread_safe after 0 seconds
	1 gem installed

Now I noticed that there is a single command to install all missing packages using ``bundle install``, sorry for the previous couple of steps.

Run the following command and enter your sudo password when it is asked.

.. code-block:: none

	$ bundle install

.. code-block:: none

	$ bundle installFetching gem metadata from https://rubygems.org/.........
	Fetching version metadata from https://rubygems.org/..
	Fetching dependency metadata from https://rubygems.org/.
	Using i18n 0.7.0
	Using json 1.8.3
	Using minitest 5.9.0
	Using thread_safe 0.3.5
	Fetching addressable 2.4.0


	Your user account isn't allowed to install to the system RubyGems.
	  You can cancel this installation and run:

	      bundle install --path vendor/bundle

	  to install the gems into ./vendor/bundle/, or you can enter your password
	  and install the bundled gems to RubyGems using sudo.

	  Password: 
	Installing addressable 2.4.0
	Using bundler 1.15.4
	Fetching colorator 0.1
	Installing colorator 0.1
	Fetching colored 1.2
	Installing colored 1.2
	Fetching ffi 1.9.10
	Installing ffi 1.9.10 with native extensions
	Fetching multipart-post 2.0.0
	Installing multipart-post 2.0.0
	Fetching gemoji 2.1.0
	Installing gemoji 2.1.0
	Fetching mini_portile2 2.1.0
	Installing mini_portile2 2.1.0
	Fetching pkg-config 1.1.7
	Installing pkg-config 1.1.7
	Using mercenary 0.3.6
	Fetching parallel 1.9.0
	Installing parallel 1.9.0
	Fetching yell 2.0.6
	Installing yell 2.0.6
	Fetching sass 3.4.22
	Installing sass 3.4.22
	Fetching rb-fsevent 0.9.7
	Installing rb-fsevent 0.9.7
	Fetching kramdown 1.11.1
	Installing kramdown 1.11.1
	Fetching liquid 3.0.6
	Installing liquid 3.0.6
	Using rouge 1.11.1
	Using safe_yaml 1.0.4
	Fetching jekyll-feed 0.5.1
	Installing jekyll-feed 0.5.1
	Fetching jekyll-paginate 1.1.0
	Installing jekyll-paginate 1.1.0
	Fetching jekyll-sitemap 0.10.0
	Installing jekyll-sitemap 0.10.0
	Fetching tzinfo 1.2.2
	Installing tzinfo 1.2.2
	Fetching ethon 0.9.0
	Installing ethon 0.9.0
	Fetching rb-inotify 0.9.7
	Installing rb-inotify 0.9.7
	Fetching faraday 0.9.2
	Installing faraday 0.9.2
	Fetching nokogiri 1.6.8
	Installing nokogiri 1.6.8 with native extensions
	Fetching jekyll-sass-converter 1.4.0
	Installing jekyll-sass-converter 1.4.0
	Fetching activesupport 4.2.6
	Installing activesupport 4.2.6
	Fetching typhoeus 0.8.0
	Installing typhoeus 0.8.0
	Using listen 3.0.8
	Fetching sawyer 0.7.0
	Installing sawyer 0.7.0
	Gem::Ext::BuildError: ERROR: Failed to build gem native extension.

	current directory:
	/tmp/bundler20170903-12379-uv1u2qnokogiri-1.6.8/gems/nokogiri-1.6.8/ext/nokogiri
	/usr/bin/ruby2.3 -r ./siteconf20170903-12379-2tgoc2.rb extconf.rb
	Using pkg-config version 1.1.7
	checking if the C compiler accepts ... yes
	Building nokogiri using packaged libraries.
	Using mini_portile version 2.1.0
	checking for gzdopen() in -lz... no
	zlib is missing; necessary for building libxml2
	*** extconf.rb failed ***
	Could not create Makefile due to some reason, probably lack of necessary
	libraries and/or headers.  Check the mkmf.log file for more details.  You may
	need configuration options.

	Provided configuration options:
		--with-opt-dir
		--without-opt-dir
		--with-opt-include
		--without-opt-include=${opt-dir}/include
		--with-opt-lib
		--without-opt-lib=${opt-dir}/lib
		--with-make-prog
		--without-make-prog
		--srcdir=.
		--curdir
		--ruby=/usr/bin/$(RUBY_BASE_NAME)2.3
		--help
		--clean
		--use-system-libraries
		--enable-static
		--disable-static
		--with-zlib-dir
		--without-zlib-dir
		--with-zlib-include
		--without-zlib-include=${zlib-dir}/include
		--with-zlib-lib
		--without-zlib-lib=${zlib-dir}/lib
		--enable-cross-build
		--disable-cross-build

	To see why this extension failed to compile, please check the mkmf.log which can
	be found here:

	/tmp/bundler20170903-12379-uv1u2qnokogiri-1.6.8/extensions/x86_64-linux/2.3.0/nokogiri-1.6.8/mkmf.log

	extconf failed, exit code 1

	Gem files will remain installed in
	/tmp/bundler20170903-12379-uv1u2qnokogiri-1.6.8/gems/nokogiri-1.6.8 for
	inspection.
	Results logged to
	/tmp/bundler20170903-12379-uv1u2qnokogiri-1.6.8/extensions/x86_64-linux/2.3.0/nokogiri-1.6.8/gem_make.out

	An error occurred while installing nokogiri (1.6.8), and Bundler cannot
	continue.
	Make sure that `gem install nokogiri -v '1.6.8'` succeeds before bundling.

	In Gemfile:
	  jemoji was resolved to 0.6.2, which depends on
	    html-pipeline was resolved to 2.4.1, which depends on
	      nokogiri

**nokogiri** has some problems.

.. code-block:: none
	
	$ sudo apt-get install zlib1g-dev

.. code-block:: none
	
	$ sudo bundle install
	Don't run Bundler as root. Bundler can ask for sudo if it is needed, and
	installing your bundle as root will break this application for all non-root
	users on this machine.
	Fetching gem metadata from https://rubygems.org/.........
	Fetching version metadata from https://rubygems.org/..
	Fetching dependency metadata from https://rubygems.org/.
	Using i18n 0.7.0
	Using json 1.8.3
	Using minitest 5.9.0
	Using thread_safe 0.3.5
	Using addressable 2.4.0
	Using bundler 1.15.4
	Using colorator 0.1
	Using colored 1.2
	Using ffi 1.9.10
	Using multipart-post 2.0.0
	Using gemoji 2.1.0
	Using mini_portile2 2.1.0
	Using pkg-config 1.1.7
	Using mercenary 0.3.6
	Using parallel 1.9.0
	Using yell 2.0.6
	Using sass 3.4.22
	Using rb-fsevent 0.9.7
	Using kramdown 1.11.1
	Using liquid 3.0.6
	Using rouge 1.11.1
	Using safe_yaml 1.0.4
	Using jekyll-feed 0.5.1
	Using jekyll-paginate 1.1.0
	Using jekyll-sitemap 0.10.0
	Using tzinfo 1.2.2
	Using ethon 0.9.0
	Using rb-inotify 0.9.7
	Using faraday 0.9.2
	Fetching nokogiri 1.6.8
	Installing nokogiri 1.6.8 with native extensions
	Using jekyll-sass-converter 1.4.0
	Using activesupport 4.2.6
	Using typhoeus 0.8.0
	Using listen 3.0.8
	Using sawyer 0.7.0
	Fetching html-pipeline 2.4.1
	Installing html-pipeline 2.4.1
	Fetching html-proofer 3.0.6
	Installing html-proofer 3.0.6
	Fetching jekyll-watch 1.4.0
	Installing jekyll-watch 1.4.0
	Fetching octokit 4.3.0
	Installing octokit 4.3.0
	Fetching jekyll 3.1.6
	Installing jekyll 3.1.6
	Fetching jekyll-gist 1.4.0
	Installing jekyll-gist 1.4.0
	Fetching jemoji 0.6.2
	Installing jemoji 0.6.2
	Bundle complete! 7 Gemfile dependencies, 42 gems now installed.
	Use `bundle info [gemname]` to see where a bundled gem is installed.
	Post-install message from html-pipeline:
	-------------------------------------------------
	Thank you for installing html-pipeline!
	You must bundle Filter gem dependencies.
	See html-pipeline README.md for more details.
	https://github.com/jch/html-pipeline#dependencies
	-------------------------------------------------

Notice the warning about running the code as root. Don't do that like me! Run without sudo as previously.

**We are done.**
