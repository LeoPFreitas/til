# Builder

**It is a creational design pattern that lets you construct complex objects step by step. The pattern allows you to 
produce different types and representation of an object using the same construction code**

## Problem

Complex objects that needs many complex steeps for construct. If you have same variations, then you extend the base 
object and add those peculiarities. Or you can create a monster constructor with all parameters and logic for 
initialize this different options. 

## Solution

Extract the object construction code out of it own class and move it to separate objects called builders.


