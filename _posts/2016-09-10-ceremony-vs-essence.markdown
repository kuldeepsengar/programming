---
layout : post
title : 'Ceremony Vs Essence'
subtitle : ''
date : 2016-09-01 00:00:00
categories : [tool]
---
> A Ceremony is the preparation, a ritual, conducted for doing a particular *thing*


-- Ceremony
```java
public class Foo{
  final Integer years;
  Integer miles;
  public Foo(years, miles){
    this.years = years; // SIN : why do you wanna use this ? can't you use maybe year1 or inputYear ???
    this.miles = miles;
  }
}

```
In Scala
-- Essence
```scala
class Foo(val years:Int, var miles:Int){

}
```
