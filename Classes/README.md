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
Method overloading means we are allowed to create multiple methods with the exact same name but with different parameters. This is useful because we can have `default parameters` meaning if a value is not given, then use the default value.

```java
class Computer {
    double screenWidth;
    double weight;
    String make;
    String model;
    String operatingSystem;

    /**
     * new constructor method that will then call the appropriate constructor
     * method depending on the arguments passed into the `this()` function
     */
    public Computer() {
      this(screenWidth, weight, make, model, operatingSystem);
    }

    /**
     * this class will need to be instantiated with the screenWidth, weight, make,
     * and model but will pass in the string "Ubuntu" without us needing to specify
     * a specific operatingSystem
     */
    public Computer() {
      this(screenWidth, weight, make, model, "Ubuntu");
    }
    
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

## Class Inheritance
What's especially magical about classes is the ability to inherit from another class. So we have this `Computer` class with it's properties and methods. Now let's say we go out and bought a computer that came with two monitors. Our `Computer` class doesn't support the `monitor` property because we assumed they only had one. This is where class inheritance, `extends`, and `super` keywords comes in.

```java
class DualMonitorComputer {
  int monitors;

  /**
   * pass in all the parameters we need for both classes. All the properties from
   * the super, or the parent class, need to be passed into the super function
   * while we still need to set the monitors property like normal
   */
  public DualMonitorComputer(screenWidth, weight, make, model, operatingSystem monitors) {
    super(screenWidth, weight, make, model, operatingSystem);
    this.monitors = monitors;
  }

  /**
   * here we call the getOperatingSystem() method from the super class by creating
   * our own version of the getOperatingSystem and returning the supers version
   * with super.getOperatingSystem()
   */
  public void getOperatingSystem() {
    return super.getOperatingSystem();
  }
}
```

## Instantiating a Class
When you instantiate a class it just means you are creating a new instance of that class. We create a new variable with a data type of the class and use the `new` keyword and call the class passing in any arguments that are required. After instantiation a class we can then call the class methods.

```java
// new instance of the Computer class
Computer myComputer = new Computer(17, 2, "Asus", "Zenbook", "Ubuntu 16.04");
myComputer.getMake();  // "Asus"

// new instance of the DualMonitorComputer class
DualMonitorComputer myDualMonitorComputer new DualMonitoryComputer(17, 2, "Asus", "Zenbook", "Ubuntu 16.04", 2);
myDualMonitorComputer.getOperatingSystem();  // "Ubuntu 16.04"
```