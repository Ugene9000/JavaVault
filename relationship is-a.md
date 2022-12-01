Inheritance defines the relationship is-a (also called the superclass-subclass relationship) between a superclass and its subclass. This means that an object of a subclass is-a superclass object, and can be used wherever an object of the superclass can be used.
Example
```Java
class Light {
}


class TubeLight extends Light {
}

class LightBulb extends Light {

}
```

```Java
Light light = new Light();
//because TubeLight is-a Light, we can write the following:
light = new TubeLight();
```

The inheritance relationship is transitive: if class B extends class A, then a class C, which extends class B, will also inherit from class A via class B.

```Java
class SpotLightBulb extends LightBulb {

}
```
The object of a SpotLightBulb _is-a_ object of a class Light.
The _is-a_ relationship does not hold between _[[peer classes]]_: an object of the LightBulb class is not
an object of the class TubeLight and vice versa.