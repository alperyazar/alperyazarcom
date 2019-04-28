qTranslate: Making Multilingual Menu URLs
=========================================

I gave a brief introduction about qTranslate plugin in my previous post. As I mentioned, it is possible to create multilingual blogs using that plugin. qTranslate allows you to convert many field of WordPress blog into multilingual forms. One of these areas is Menus, found in Appearance -> Menus inadministrator panel. If your theme supports Menus, you can easily create navigation menus from there. If you are creating menus by that way, you are on the right road. :) Otherwise, following content is not applicable for you if you are creating navigation menus by editing theme files.Although it is easy to create multilingual "Link Names" via administrator panel, it is not easy to assign different URLs for different languages. You can't simply enter URLs similar to given one in URL area:

.. code-block:: none

  [:Lang1]http://www.lang1link.com[:Lang2]http://www.lang2link.com

When you enter a URL similar to that format, most probably a URL filter in WordPress detecets it as an invalid URL (as expected). As a result, an empty text is saved into database instead of entered URL. One possible solution may be disabling URL filter by changing core codes of WordPress or finding a plugin for that purpose. But I preferred to add URL to database directly, not over the administrator panel. You can view and edit database thru panel like phpMyAdmin. URLs of Menus are stored in "postmeta" table of WordPress. If you didn't change prefix of tables, full name of table should be "wp_postmeta". You will see many entries in that table. "meta_key" value of URLs is "_menu_item_url". With some search, you can find entry of desired URL. By changing entry similar to given format, it is possible change URL of link according to language. Lang1 and Lang2 are codes of your languages. For example: en for English, tr for Turkish. When your visitors browse your site in Lang1, link will open to www.lang1link.com and in Lang2, link will open to www.lang2link.com. Note that it is possible to view modified URL by visiting Appearance -> Menu. However, you shouldn't modify URLs from administrator menu. Otherwise, URL filter of WordPress detecets modified URL as invalid URL again. :) 

Updated: -

Created: July 08, 2012
