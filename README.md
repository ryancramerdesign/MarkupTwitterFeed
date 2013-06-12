# MarkupTwitterFeed

---------------------------------------------------------------------

### Module that generates an HTML list for a Twitter feed and caches it. 

Use this to show a Twitter feed on your ProcessWire-powered website. 

This module uses the [tmhOAuth](https://github.com/themattharris/tmhOAuth) library by @themattharris.
This library is included with the MarkupTwitterFeed module files.

## To Install or Upgrade

Whether installing or upgrading, the process will be the same. 
If you already have the old MarkupTwitterFeed module installed, you do not need to uninstall it--
you can just replace the files. Follow the steps below to install or upgrade:

- Place the module files in `/site/modules/MarkupTwitterFeed/`
- In ProcessWire admin, go to *Modules > Check for new modules* and click *install* for *Twitter Feed Markup*.
- Note the Twitter API settings on the settings screen. To obtain these, create a new Twitter application at: [https://dev.twitter.com/apps](dev.twitter.com/apps). Once created, copy and paste the settings to the module configuration.

## Usage

Basic example:
```
$t = $modules->get('MarkupTwitterFeed'); 
echo $t->render(); 
```

Specifying options example:
```
$options = array(
  'limit' => 3, 
  'cacheSeconds' => 600, // 10 minutes
  'showDate' => 'before'
  ); 
$t = $modules->get('MarkupTwitterFeed'); 
echo $t->render($options);
```

### All available options

Default values are shown below. 

```
$t->limit = 3; 			// max items to show
$t->cacheSeconds = 3600; 	// seconds to cache the feed (3600 = 1 hour)*
$t->dateFormat = 'F j h:i a';	// PHP date() or strftime() format for date field: December 4, 2013 1:17 pm
$t->linkUrls = true; 		// should URLs be linked?
$t->showHashTags = true; 	// show hash tags in the tweets?
$t->showAtTags = true; 		// show @user tags in the tweets?
$t->showDate = 'after';		// show date/time: 'before', 'after', or blank to disable.
$t->showReplies = false;	// show Twitter @replies in timeline?
$t->showRetweets = false;	// show Twitter retweets in timeline?
$t->timeline = 'user_timeline'; // what timeline to show: mentions_timeline, user_timeline, home_timeline or retweets_of_me
$t->screenName = '';		// screen name to return results for (default=blank, Twitter default)
$t->consumerKey = '';		// Twitter API consumer key*
$t->consumerSecret = '';	// Twitter API consumer secret*
$t->userToken = '';		// Twitter API access/user token*
$t->userSecret = '';		// Twitter API access/user secret*

// markup options:
$t->listOpen = "<ul class='MarkupTwitterFeed'>";
$t->listClose = "</ul>";
$t->listItemOpen = "<li>";
$t->listItemClose = "</li>";
$t->listItemDateOpen = "<span class='date'>";
$t->listItemDateClose = "</span>";
$t->listItemLinkOpen = "<a href='{href}'>";
$t->listItemLinkClose = "</a>";
```

*\*Note that the default value of these options is configured from the MarkupTwitterFeed module settings screen.*

