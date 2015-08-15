# Changelog #

## Version 1.7 ##

  * New language: French
  * New language: Spain
  * New language: Czech
  * New icon caching (all favicons will be collected and loaded in one image file)
  * Minify and compression of JavaScript and CSS files
  * Performance improvements (speedup page loading)
  * Selecting starred items will now remove unread filter
  * New json interface (currently undocumented)
  * Bugfix: missing logger definition in opml import ([issue 42](https://code.google.com/p/rsslounge/issues/detail?id=42))
  * Bugfix: fix OPML import bug: opml files which uses "title" instead of "text" for the feed item title will now be fetched correctly
  * Bugfix: set default charset of database to utf8
  * Bugfix: fix heise plugin (works now with utf8 encoded database)
  * Bugfix: icon file type detection ([issue 58](https://code.google.com/p/rsslounge/issues/detail?id=58))

## Version 1.6 ##

  * New header design
  * Bugfix: login works now correct
  * Select images on mouseover
  * Prevent get\_browser error if no browsercap.ini is set

## Version 1.5 ##

  * Bugfix: usage of database prefix will now work

## Version 1.4 ##

  * Design improvements: new dropdown menues for filter settings
  * New order option by feed priority
  * rsslounge works now on IE7+
  * rsslounge works now on iPad
  * New setting for choosing whether all items will be shown opened or closed per default
  * New public mode for guest. rsslounge shows all items also for non authenticated users and allows any non editing action.
  * Enable usage of port in database connection setting (e.g. 127.0.0.1:3306) ([issue 23](https://code.google.com/p/rsslounge/issues/detail?id=23))
  * Starred items will not be deleted
  * New robots.txt prevents search engine indexing
  * New datasource plugin for flickr
  * New datasource plugin for zeit.de (full content)
  * Smaller package size (unused Zend Frameworks components removed)
  * Cleanup old errormessage entries
  * Bugfix: items without title will get the title "[item](no.md)"
  * Bugfix: allow Umlaute in Feed names
  * Bugfix: calendar works now also after clicks on the month overview
  * Bugfix: solved UTF8 issue on ajax communication
  * Bugfix: fix translation issue ([issue 26](https://code.google.com/p/rsslounge/issues/detail?id=26))
  * Bugfix: parallel refresh (cronjob and ajax) results in double update. Now no ajax refresh appears when cronjob was running.
  * Bugfix: just one refresh of item list on calendar toggle
  * Bugfix: set priority range after feed delete


## Version 1.3 ##

  * New: [Shortcuts](Shortcuts.md) available
  * New Setting: open links in new window
  * New Setting: define an anonymizer service
  * More detailed debug log messages for feed updates
  * Set a bigger timelimit for multimedia feeds which nees more time for fetching images
  * New Config Params for enable/disable cache
  * New Config Params for cache pathes
  * Impromptu update from 2.7 to 2.8
  * Wideimage update from 1.0 beta 2 to 9.09.04
  * Zend Framework update from 1.9.7 to 1.10.1
  * Bugfix: show correct amount of starred items after mark a single item ([issue 10](https://code.google.com/p/rsslounge/issues/detail?id=10))
  * Bugfix: using the bookmarklet for adding feeds will now take over the complete url ([issue 9](https://code.google.com/p/rsslounge/issues/detail?id=9))
  * Bugfix: wrong title for mark as read removed ([issue 8](https://code.google.com/p/rsslounge/issues/detail?id=8))
  * Bugfix: seleting correct language in installation script
  * Bugfix: get correct installed database version
  * Bugfix: on some rare situations the settings will not be written back correctly on first run after installation
  * Bugfix: correct image frame height in safari
  * Bugfix: images in entries by heise are working now
  * Bugfix: mark photos as read which was loaded by "more" will now work correctly


## Version 1.2 ##

  * Zend Framework update from 1.9.6 to 1.9.7
  * jQuery update from 1.3.2 to 1.4
  * Small design improvement
  * Portuguese language files (thanks to Jonnathan Soares Lima!!)
  * Bugfix: show 0 on no unread items in category
  * Bugfix: htmlurl exception
  * Bugfix: wrong filter handling


## Version 1.1 ##

  * Bugfix: Language support