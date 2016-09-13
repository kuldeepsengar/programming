---
layout : post
title : 'Processing'
subtitle : 'A language for the designers'
date : 2016-09-10 00:00:00
categories : [tool]
---

## What is Processing
Processing is a language for the designers to build visual art through programming. It is like a sketchbook for the programmers to draw.


## Download
You can download processing from [here](https://processing.org/download/).

> It is always good to donate for the things you appreciate

## Installation
You just need to extract the zip and start using processing.


## Simple program to draw

~~~~
int getRandomCoordinate(){
  return int(random(600));
}
int getRandomColor(){
  return color(random(0,255),random(0,255),random(0,255));
}
void setup(){
  size(600,600);
  background(0);
}
void draw(){
  stroke(getRandomColor());
  line(300,300,getRandomCoordinate(),getRandomCoordinate());
}
~~~~

> Run this code and see the result yourself
