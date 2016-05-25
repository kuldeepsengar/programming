---
layout : post
title : 'Default methods in Interface'
subtitle : 'Why and how'
date : 2016-05-23 00:00:00
categories : [tool]
---

## What is default method
In Java 8, Oracle has included *Default Methods* or *Defending Methods* for Interfaces. This allows Evolution of Interfaces by giving a default method in case the implementing classes don't provide the implementation.

#Why ?
Consider a scenario where you have published your API, with the following Interface

```java
public interface A {
  public void doA();
}
```

There is client, let's say **UserOfA**, who uses your API and have implemented your Interface

```java
public class AImpl {
  public void doA(){
    System.out.println("I'm doing A");
  }
}
```

Now you want to release new version of API having changes in *Interface A*

```java
public interface A {
  public void doA();
  public void doB();
}
```

For your client **UserOfA** to start using your API, it needs to update it's implementing class for no good reason.

Default methods allow your Interface to provide a default implementation of the method, so that the client using the interface need not have to go to hassle by changing their code base (for the method they might not even need).

## How ?
You can evolve your Interface in the following fashion ::
```java
public interface A {
  public void doA();
  default void doB() {
    System.out.println("I'm doing B, but you can change it if you want");
  }
}
```

Now the client **UserOfA** is happy that it doesn't have to evolve with you immediately.

> Default methods achieves ** Backward Compatibility ** very easily


## Difference between Abstract Class and Interface ?
With the default method coming into picture, it might look like there is no difference between Abstract class and Interface, But there is.
Abstract can have a constructor, therefore has a state associated with it. Interface default method has no reference to a particular implementation state.

##Multiple Inheritance
A class can implement more that one interface is well known. But what if two classes evolve at the same time to have exact same default method, how will the class behave now ?
let's take an example :

```java
public Interface A {
  default void doSomethingAwesome(){
    System.out.println("I'm doing Awesome");
  }
}

public Interface B {
  default void doSomethingAwesome(){
    System.out.println("I'm also doing Awesome");
  }
}

public class C implements A, B {

}
```

What will be the output of the following ? The answer is : * it will not compile saying class C inherits unrelated defaults for doSomethingAwesome() for types A and B

To fix this error, the class then needs to implement the method in the class too.

```java
public class C implements A,B {
  public void doSomethingAwesome(){
    System.out.println("I'm here to resolve the ambiguity");
  }
}

```

### super for Interface default methods
We can call the default method using the **super** keyword in the following way :
```java
public class C implements A, B {
  public void doSomethingAwesome(){
    A.super.doSomethingAwesome();
  }
}
```


## Where from here ?
Today I was watching the Java 9 & Beyond by *Mark Reinhold*, and he mentioned that many features, including default methods, in Java 8 are added in a purview of Java 9, Valhalla, Panama projects.
For example a speculative feature of having **value** in addition to **classes** to represent values, which would require something like default methods for evolvability and backward Compatibility.
