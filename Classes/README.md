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

## Composition vs Inheritance
Composition is creating a class as a member, or a property/field, inside of another class. For example, a room can contain furniture but the room is not the furniture itself. The room will have paint on the walls, but the room is not the paint. The benefits of using composition over inheritance is

**Flexibility**: Java does not support multi-class inheritance which means we can only inherit from a single class. With composition we are not stuck with trying to decide whether our class is specifically one thing but instead it is made up of multiple things or classes.

**Specificity**: What I mean by specificity is that when creating classes as a property we can then become more specific as to what each property contains. In our Room example, the Room can contain a nightstand of class `Furniture`. With composition we can then instantiate this `Furniture NightStand` class and using the constructor function for the `NightStand` we can specify things like the number of legs, color, or material it is made of.

```java
// Furniture class
class Furniture {
  int legs;
  String color;
  String material;

  public Furniture(int legs, String color, String material) {
    this.legs = legs;
    this.color = color;
    this.material = material;
  }
}

// Room class
class Room {
  Furniture nightStand;

  public Room(Furniture nightStand) {
    this.nightStand = nightStand;
  }
}
```

If we wanted, we could get even more specific by creating a `PaintColor` class and giving it properties like `String brand`, `String color`, `boolean hasLead` and so on.

## Encapsulation
Encasulation in a nutshell is restricting properties and fields from outside use from within a class. Let's take a look at an example where we are NOT using encapsulation.

```java
class Hero {
  String name;
  int health;
}
```

In our `Hero` class we aren't specifying whether or not the properties on the class are public, protected, or private, also known as scope, so by default Java will make these properties public or available for anyone to use.

```java
Hero ragnar = new Hero();
ragnar.name = "Ragnar";
ragnar.health = 100;
```

We are able to manipulate the values of our `Hero` class instance and there are no constrains to the values passed in, other than the data types. What if our hero were to lose all his health? The player could easily access the hero's health property and change it back to 100 or even 1000. Now let's take a look at how to properly use encapsulation.

```java
class Hero {
  private String name;
  private int health;

  public Hero(String name, int health) {
    this.name = name;
    this.health = health;
  }

  public getHealth() {
    return this.health;
  }

  public getName() {
    return this.name;
  }
}
```

By specifying that the properties on our `Hero` class are `private` scope we are restricting access to the `name` and `health` property to only inside the `Hero` class. This way, players can only view the name and health of a particular hero but they are not able to change them.

#Polymorphism
Polymorphism isn't as magical as it sounds and is actually quite simple. Polymorphism changes the way a method behaves depending on the object it is being called from.

```java
class Character {
  public String greeting() {
    return "I am just an NPC";
  }
}

class PlayableCharacter extends Character {
  @Override  // not required but good to let others know this method isn't original to the current class
  public String greeting() {
    return "I am a Playable Character";
  }
}

class NonPlayableCharacter extends Character {
  // we are not overriding the greeting() method from Character
}

PlayableCharacter myPC = new PlayableCharacter();
myPC.greeting()  // "I am a Playable Character"

NonPlayableCharacter myNPC = new MyPlayableCharacter();
myNPC.greeting()  // "I am just an NPC"
```

# Java Classes Pt. 2

## Interfaces
Interfaces are like classes that have no logic inside of them. Atleast, this was true up until Java-8. Since Java-8 we can now write `default` and `static` methods in our interfaces that contain logic.