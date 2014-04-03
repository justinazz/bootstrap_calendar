#Bootstrap Calendar

A simple calendar plugin for jQuery and Twitter Bootstrap.

_Works inline, in dropdowns, and in the responsive navbar!_

##Dependencies
- [jQuery 1.7.2+](http://jquery.com/)
- [Twitter Bootstrap 2.x](http://getbootstrap.com/2.3.2/)

##Options
- popover_options ([Bootstrap popover](http://getbootstrap.com/2.3.2/javascript.html#popovers) object)
- tooltip_options ([Bootstrap tooltip](http://getbootstrap.com/2.3.2/javascript.html#tooltips) object)
- days (array)
	- default: default: ["S", "M", "T", "W", "T", "F", "S"]
- months (array)
	- default: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"]
- show_days (boolean)
	- default: true
- req_ajax (object)
	- req_ajax.type (string) {'get', 'post'}
	- req_ajax.url (string)
- events (array of event array)
	- req_ajax.type (string) {'get', 'post'}
	- req_ajax.url (string)
	- req_ajax.data (object)
		- allows user to add additional data to the asynchronous request in addition to the hard coded 'year' and 'month' parameters
- Event (array)
	- 0 (string): date
	ex: "17/4/2013"
	- 1 (string): title
	ex: "hello world!"
	- 2 (string): link
	ex: "http://github.com"
	- 3 (string): color
	ex: "#333"
	- 4 (string): html popover
	ex: "Text for the content of popover...description of event...image..."
- monday_start_of_week (boolean)
	- default: false
	- sets if Monday is to be start of week, otherwise Sunday
- event_custom_css_class (string)
	- default: "event"
	- allows the user to override the css class that is assigned by default to each event
- left_icon_custom_css_class (string)
	- default: "icon-arrow-left"
	- allows overriding of icon of left icon css class
- right_icon_custom_css_class (string)
	- default: "icon-arrow-right"
	- allows overriding of icon of right icon css class

##Use example

_Note: that each event in the example has a diferent behavior_

The blue event has a hover popover
```javascript
array(
	"27/4/2013", 
	'github drinkup', 
	'https://github.com/blog/category/drinkup', 
	'blue'
)
```

The green event has a click popover
```javascript
array(
	"7/4/2013", 
	'bootstrap logo popover!', 
	'#', 
	'#51a351', 
	'<img src="http://bit.ly/XRpKAE" />'
)
```

The red event has a hover tooltip
```javascript
array(
	"17/4/2013",
	'octocat!', 
	'https://github.com/logos', 
	'red', 
	'new github logo <img src="http://git.io/Xmayvg" />'
)
```

###Javascript:
```javascript
$(document).ready( function(){

	theMonths = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];
	theDays = ["S", "M", "T", "W", "T", "F", "S"];

    $('#calendar_test').calendar({
        months: theMonths,
        days: theDays,
        req_ajax: {
        	type: 'get',
        	url: 'json.php'
        }
    });
});
```
						

###PHP:
```php5
<?php
$month = isset($_GET['month']) ? $_GET['month'] : date('n');
$year = isset($_GET['year']) ? $_GET['year'] : date('Y');

$array = array(
  array(
    "7/$month/$year", 
    'bootstrap logo popover!', 
    '#', 
    '#51a351', 
    '<img src="http://bit.ly/XRpKAE" />'
  ),
  array(
    "17/$month/$year", 
    'octocat!', 
    'https://github.com/logos', 
    'blue', 
    'new github logo <img src="http://git.io/Xmayvg" />'
  ),
  array(
    "27/$month/$year", 
    'github drinkup', 
    'https://github.com/blog/category/drinkup', 
    'red'
  )
);

header('Content-Type: application/json');
echo json_encode($array);
exit;
?>
```

##Credits
original [bic_calendar](https://github.com/bichotll/bic_calendar) by [bic.cat](http://bic.cat/).

[bootstrap_calendar](https://github.com/xero/bootstrap_calendar) fork (english localization and updates) by [xero](http://xero.nu/)
