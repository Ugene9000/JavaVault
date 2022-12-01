whereas inheritance defines the relationship is-a between a superclass and its subclasses, [[aggregation]] defines the relationship has-a (also known as whole-part relationship) between an instance of a class and its constituitents (also called parts)
```Java
class Light {

int noOfWatts;
private boolean indicator;
protected String location;

}
```

An instance of class Light _has_ (or _uses_) the following parts:
- a field to store its wattage (noOfWatts)
- a field to store whether it's on or off (inficator)
- a String object to store its location (denoted by field reference location)
In Java, a composite object cannot contain other objects. It can only store _reference values_ of its constituitent objects in its fields.

This relationship defines an _[[aggregation hierarchy]]_ that embodies the _has-a_ relationship