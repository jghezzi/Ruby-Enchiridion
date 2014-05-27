---
title: AJAX
date: 2014-05-25 
---

###Summary
AJAX (Asynchronous Javascript and XML) is a development technique that allows web applications to send and receive server data without requiring a reload of the active web page. This "asynchronous" approach allows developers to update only certain sections of the current web page, resulting in a user experience that mimics the responsiveness of a desktop application. 

AJAX may send / receive data in XML, JSON, HTML and other formats. It can be directly accessed using established JQuery methods ($.ajax(), $.get(), $.post(), etc.) and paired with Javascript to allow update of specific page elements.

Here's a basic AJAX call using the JQuery method '$.ajax()' to update an item on the server:

>	$('.update-button').on('click', function(e){
>	 var updated_item_text = $('#items_name').val()
>
>	 $.ajax({			
>	  url:	"/items/" + update_id,
>	  type:	'PATCH',
>	  data:{ item:{ "name":  updated_item_text } };
>	 });
> });

In this example, the value of the '#items_name' ID is assigned to the updated_item_text variable, which is used to update the item instance on the server.

###Tips

* AJAX events may be used to mark when requests have been sent, completed or resulted in error. These events may be monitored either locally or globally and should be included as part of all AJAX calls to ensure errors are properly handled by the application.

* The 'serialize()' function is useful for gathering input elements in a large form. Rather than extracting each individual input value from a form, 'serialize()' extracts all input elements at once, organizing them as a text string that can then be POSTed to the server within AJAX.

* Upon completing a server action (.on('ajax:complete')), AJAX will return several arguments, including a JSON data object that can be received and processed such that all attributes are accessible through object notation:

>	$('#new_item').on('ajax:complete', function(event, data, status, xhr) {
>	  var item = data.responseJSON.item,
>		name = item.name;

* Developers using AJAX should make accommodations for browsers that have disabled JavaScript, substituting standard HTML form behavior instead.

* Users may not be able to determine that their form submission is complete and successful using AJAX. Developers should leverage AJAX messages ('ajax:complete') to advise users of success and failure.


###Resources

Documentation on AJAX with JQuery. Concise docs with a good code examples: [AJAX Docs](http://api.jquery.com/category/ajax/)

Early article on AJAX from 2005. Not terribly informative, but interesting to see the enthusiasm and how deeply Google was invested: [Web Archive on AJAX](https://web.archive.org/web/20080702075113/http://www.adaptivepath.com/ideas/essays/archives/000385.php)

Some AJAX pitfalls to avoid: [AJAX Mistakes](https://alexbosworth.backpackit.com/pub/67688)

Detailed developer docs from Mozilla: [Mozilla](https://developer.mozilla.org/en-US/docs/AJAX)

