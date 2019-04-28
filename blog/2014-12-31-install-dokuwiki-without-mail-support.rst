Install Dokuwiki Without Mail Support
=====================================

`Dokuwiki <http://www.alperyazar.com/apps/redirect/tcEov>`__ is great. But it requires mail() PHP function for registration or subscriptions. However, depending on your needs you don't have to use mail feature of dokuwiki. For single user, or registration closed typed wikis mailing is not essential. You may want to install Dokuwiki on a server where mail() function is not available.  Some hosting providers may disable mail() function. When you try to install Dokuwiki, it gives you an error something like that:

.. code-block:: none

  PHP function mail is not available.

install.php doesn't allow you to install Dokuwiki. To fix this problem, ( for **2014-09-29b "Hrun"**)

1. Open your install.php
2. Locate check_function around line 554.
3. Find mail in explode(' ', 'addslashes call_user_func .... ini_get mail mkdir ...');
4. Delete mail from that text. (Put a space between ini_get and mkdir, not ini_getmkdir !)
5. Save your install.php
6. Now, install your Dokuwiki

Don't forget that Dokuwiki still is not able to send mails. This steps just allow us to skip checking mailing feature on installation.

Updated: -

Created: December 31, 2014
