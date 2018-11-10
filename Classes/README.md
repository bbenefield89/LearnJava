# Java Classes

## Creating a simple class
To create a class in Java it only needs the keyword `class`, a name, and some curly braces

```java
class Computer {}
```

This is what a very basic class would look like with properties and methods that `get` the value and `set` the value of a particular property. These are also known as `Getters` and `Setters`.

```java
class Computer {
    double screenWidth;
    double weight;
    String make;
    String model;
    String operatingSystem;

    public double getScreenWidth() {
        return screenWidth;
    }

    public void setScreenWidth(double screenWidth) {
        this.screenWidth = screenWidth;
    }

    public double getWeight() {
        return weight;
    }

    public void setWeight(double weight) {
        this.weight = weight;
    }

    public String getMake() {
        return make;
    }

    public void setMake(String make) {
        this.make = make;
    }

    public String getModel() {
        return model;
    }

    public void setModel(String model) {
        this.model = model;
    }

    public String getOperatingSystem() {
        return operatingSystem;
    }

    public void setOperatingSystem(String operatingSystem) {
        this.operatingSystem = operatingSystem;
    }
}

```

## Constructor Methods
Constructor methods allow us to give the properties in our class some value when we instantiate, create a new instance of, the class instead of having to always call the `Setter` methods.

```java
class Computer {
    double screenWidth;
    double weight;
    String make;
    String model;
    String operatingSystem;

    public Computer(double screenWidth, double weight, String make, String model, String operatingSystem) {
        this.screenWidth = screenWidth;
        this.weight = weight;
        this.make = make;
        this.model = model;
        this.operatingSystem = operatingSystem;
    }

    /**
     * methods go down here
     */
```

## Method Overloading
Method overloading means we are allowed to create multiple methods with the exact same name but with different parameters. 