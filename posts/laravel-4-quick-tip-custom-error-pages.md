title: Laravel 4 Quick Tip: Custom Error Pages
slug: laravel-4-quick-tip-custom-error-pages
status: published
date: May 2 2013 10:06
tags: quick-tip, laravel
-------
Here's a quick tip on how to create custom error pages in Laravel 4. Laravel has a default built-in event listener for errors attached to the application instance. You can pass it a callback which will provide you with two variables, the exception and the error code.<!--more-->

~~~ .php
App::error(function($exception, $code)
{
	switch ($code)
	{
		case 403:
			return Response::view('errors.403', array(), 403);

		case 404:
			return Response::view('errors.404', array(), 404);

		case 500:
			return Response::view('errors.500', array(), 500);

		default:
			return Response::view('errors.default', array(), $code);
	}
});
~~~

This provides a very easy way to create custom error pages for your application.

Edit: Edited the view response for providing the correct HTTP status code. Thanks [Holger Weis](https://twitter.com/betawax)!