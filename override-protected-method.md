---
layout: default
title: Override Protected Method
date: 2024-12-28
categories: OOPS Concepts
---
# Overriding A Protected Method In PHP
Published on 2024-12-28

It is possible to override a protected method in object-oriented programming (OOP) languages like PHP. Here's an explanation of why it is allowed and why you might want to override a protected method.

**Why can a protected method be overridden?**
In OOP, protected methods are designed to be accessible within the class where they are declared and in any subclass that extends the parent class. This access control strikes a balance between full encapsulation (private) and open access (public).

***Purpose of protected***: It allows controlled access to methods for extending functionality in derived (child) classes while still hiding them from external code.

***Why overriding is allowed***: Since protected methods are specifically intended to be accessed in subclasses, overriding them gives child classes the ability to customize the behavior of inherited functionality.

**Why would you override a protected method?**

Overriding a protected method is useful when you need to extend or modify the behavior of a method from the parent class in the context of a subclass. Here are some reasons why you might do this:

***Specialization of behavior in child classes***
When a subclass represents a more specific version of the parent class, it often needs to tweak or replace the inherited behavior to better align with its specialized functionality.

***Example***: A Shape class might have a calculateArea method that is overridden in subclasses like Circle or Rectangle to calculate the area based on the specific shape.

***Adhering to polymorphism principles***
Polymorphism allows objects of different subclasses to behave differently for the same method call. Overriding a protected method in a subclass ensures that the correct behavior is invoked for that subclass while maintaining encapsulation.

***Avoiding code duplication***
Overriding allows subclasses to reuse parts of the parent's implementation while extending or modifying it, reducing code duplication and ensuring maintainability.
 
***Maintaining encapsulation***
Overriding protected methods keeps the overridden method hidden from external code while still allowing the parent-child relationship to work seamlessly. This helps ensure that the method’s access level remains consistent across the hierarchy.

**Example**
```php
<?php

class A{
	function __construct(){
		echo 'constructor called...'.PHP_EOL;
	}
	protected function m(){
		echo 'A method';
	}
	public function show(){
		$this->m();
	}
}

class B extends A{
	protected function m(){
		echo 'B method'.PHP_EOL;
	}	
}

$obj = new B();
$obj->show();

```
**Real-world analogy**
Imagine you have a base blueprint for building houses with a protected section for utilities (e.g., wiring, plumbing). Each specific house design (subclass) can tweak or replace the utility layout (override the protected method) to better suit the specific requirements of the house while still inheriting the core layout from the base blueprint.

**Conclusion**
Overriding a protected method is an essential feature in OOP because it combines the benefits of inheritance, encapsulation, and polymorphism. It allows child classes to specialize or enhance the behavior of a parent class while maintaining controlled access and avoiding code duplication.

Let me know if you'd like more examples or deeper insights!
