# Documenting Reflection Method Class

This class is designed to parse and tokenize a PHP DocBlock for a class method.  This is useful because it
enables you to add custom annotations to your methods for various uses.

Personally, I've used it to help create rails-style helper classes in my frameworks.  I use smarty as my 
template rendering engine, and use helper classes to create template functions, modifiers and blocks.  By 
using a custom annotation (@helperType) in my DocBlocks, I can properly register the class method of a helper
as a function, modifier or block.

## Usage

Usage is pretty simple, you just need to do a bit of reflecting.  Say you had a class that looks like:

<pre>
class Foo
{
	/**
	 * Does Something
	 *
	 * @someAnnotation FooBar
	 * @return void
	 */
	public function bar ()
	{
		// do stuff
	}
}
</pre>

You could get the tags, and annotation as a result, by doing the following 
(assuming you've included the DocumentingReflectionMethod class):

<pre>
$rc 		= new ReflectionClass('Foo');
$instance 	= $rc->getInstance();
$docs		= new DocumentingReflectionMethod($instance, 'bar');
$tags		= $docs->getTags();

if (isset($tags['someAnnotation']))
{
	// do whatever you want
}
</pre>

## Other Info

The class itself is pretty well-documented, so you shouldn't have much trouble figuring things out.  If
you want some brownie points, you could always create /edit wiki pages for various pieces of functionality, and
if you need help / found a bug, file a ticket in the [issues](http://github.com/masterexploder/DocumentingReflectionMethod/issues)