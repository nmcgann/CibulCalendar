# Overview

**NM Modified version**  
See `newfeatures.html` for a demo of the new feature ideas in action.  
(note the old examples need their css changing to handle the new prev / next year features - not done yet)

**Changes are:**  
* fixed the obvious bugs in the other issues (the Feb 2016 and related things)  
* added year prev / next buttons.  
* modified the factory (setCibulCalendar) to instantiate immediately and return the calendar object so methods like setSelected can be called on it. (rather than instantiate the object via new CibulCalendar in a div which is awkward to integrate).  
* modified the `_init` method to update the input field value and fire change if there is a selected option.  
* fixed the basic css up a bit (z-index etc.).  
* Temporarily commented out non-english built-in language strings.  

**Old info:**

CibulCalendar is a date picker that enables users to easily pick dates or date ranges.

Here is the simplest way to get it running:

`function onload() {
  setCibulCalendar('basic'); // will stick to element <input type="text" id="basic"/>
}`

You can see used [here](https://cibul.net/pepite/fr)

Features include:

* Drag and drop range selection
* Single date selection
* Multilingual
* Helper function for single line setup
* Fully Customizable (see details below)

How to use

The script can be used directly in the browser or using CommonJs or AMD

Browserify example (CommonJs): `var cLib = require('./CibulCalendar/src/CibulCalendar') )`

There are two ways to use the calendar:

The easiest way is to use the helper function to bind the calendar to an input field:

`setCibulCalendar(id, options)`

But you might want to handle the Calendar in a script rather than applying it directly on an input field, in which case you should use:

`var cCal = new CibulCalendar(canvasElem, options)` 

# Options

* **init** (default: today): date defining initially displayed month
* **range** (default: true): if false, range date picking is disabled. Here is an example.
* **enabled** (default: true): state of the calendar at init
* **lang** (default: ‘en’): Language of the calendar. can be english (en), french (fr), italian (it) or spanish (es). You can extend this with any other language (see below).
* **firstDayOfWeek** (default: 1): first day of the week on the calendar. 0 for sunday and onwards.
* **selected** (default: false): default selection at initialization. Should be a object: {begin: Date, end: Date}
* **filter**: (default: false): callback called on each calendar render to handle date classes. If set, function is given a date and an array of classes and should return the array of classes that will be set on the rendered calendar. Click here for an example highlighting weekends.
navDomContent (default: {prev: ‘<', next: '>‘}): html content for the month navigation links. In case you want to set something more fancy like icons or images.
* **classes**: in case you want to change the name of the classes used in the calendar.
* **monthNames**: add a new month set in the language of your choice. See here for an example of a calendar in icelandic
* **weekDays**: add a new week set in the language of your choice
* **switchMonthOnHoverDelay**: on a range selection spanning over multiple months, the delay during which next month days should be hovered over before the calendar goes to the neighboring month

# Methods

* **disable**: disable the calendar
* **enable**: enable the calendar
* **showNext**: render following month
* **showPrevious**: render previous month
* **setSelected(newSelection, updateMonth)**: set new selection. newSelection is an object containing two indexes: begin and end, each referring to a date.
* **updateMonth** is a boolean indicating if the month of the start of the selection should be displayed.
