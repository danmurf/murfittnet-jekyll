---
layout: post
identifier: "blog125"
title: "Creating immutable objects in PHP"
date: "2019-01-27 20:00:00 +0000"
tags: [ "PHP", "Object Oriented Programming" ]
permalink: "blog/creating-immutable-objects-in-php"
---
You may have seen the `\DateTimeImmutable` class being used, and wondered why is this different from the `\DateTime` class? I guess it's the same...but immutable, right? Why would I want to use an immutable object? Here's a brief overview.

## Why use an immutable class?

In php, when you pass around an object by assigning it to a variable, you are actually creating another *reference* to that object, rather than creating another version of it.

```php
$person1 = new Person;
$person2 = $person1;

$person2->setName('Jessie Wongus');

echo $person1->getName(); // Jessie Wongus
```
You can see from the example above, that when we created `$person2` we just referenced `$person1`. This means they don't just share the same state, but they are actually the same object; the same data in memory. Now, you're unlikely to write code like the example above, but it might start to become apparent of the possible problems when using fluent setters. Here's another example:

```php
$startTime = new \DateTime('now');
$endTime = $startTime->add(new \DateTimeInterval('P1D'));
```
This will create a new start time, of now, and then create a new end time which is 1 day after the start time. But wait...we created the new end time by assigning it the value returned from `$startTime->add()`. This both added an interval to the start time *and* returned itself. This means that if we output the value of `$startTime`, it will be 1 day from now.
```php
echo $startTime->format('d m Y'); // 1 day from now
```
At this point, `$startTime` and `$endTime` are effectively the same. The way we get around this is to use a class which creates an immutable object. As it happens, there is a `/DateTimeImmutable` class just right for the job.
```php
$startTime = new \DateTimeImmutable('now');
$endTime = $startTime->add(new \DateTimeInterval('P1D'));
```
## How do you create an immutable class?
An immutable class is no different than any other class, apart from the state can never be changed. Each time you want to change the value of a particular property, a new object is returned with the new value. For example:

```php
class MyImmutableClass
{
    private $name;
    private $flavour;

    public function __construct($name)
    {
        $this->name = $name;
    }

    public function withName($name)
    {
        $new = clone $this;
        $new->name = $name;

        return $new;
    }

    public function withFlavour($flavour)
    {
        $new = clone $this;
        $new->flavour = $flavour;

        return $new;
    }
}
``` 
Also note that the setter methods are prefixed with `with` rather than `set`. This is a common convention when creating immutable objects.  These immutable objects are also known as a [value objects][1], as any two objects are never the same (one does not equal the other), even though the values or state that they represent could be.
```php
// The values or state may be the same
$valueObject1->getValue() === $valueObject2->getValue();

// But they are never the same instance
$valueObject1 !== $valueObject2;  
```
I hope you found this helpful. Let me know in the comments any thoughts or questions about value objects or immutability.

[1]: https://en.wikipedia.org/wiki/Value_object