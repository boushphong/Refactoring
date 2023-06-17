# Primitive Obsession

## BAD CODE
**Why:**
- In the below code, the engine-related information (`engineType` and `engineHorsepower`) is represented using primitive types (`String` and `int`). This is an example of "primitive obsession," where the code relies on primitive types to represent a concept that could benefit from a dedicated custom object.

```java
class Vehicle {
    private String make;
    private String model;
    private int year;
    private String color;
    private int mileage;
    private String engineType;
    private int engineHorsepower;
    
    // Constructors, getters, and setters
    
    public void printInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
        System.out.println("Color: " + color);
        System.out.println("Mileage: " + mileage);
        System.out.println("Engine: " + engineType + " (" + engineHorsepower + " HP)");
    }
}
```

# Custom Object - Refactoring Technique

## GOOD CODE
**Why:**
- The engine information is encapsulated within the `Engine` object, which provides a more structured and maintainable approach.
```java
class Vehicle {
    private String make;
    private String model;
    private int year;
    private String color;
    private int mileage;
    private Engine engine;
    
    // Constructors, getters, and setters
    
    public void printInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
        System.out.println("Color: " + color);
        System.out.println("Mileage: " + mileage);
        System.out.println("Engine: " + engine.getDescription());
    }
    
    // Custom object representing the engine
    public static class Engine {
        private String type;
        private int horsepower;
        
        // Constructors, getters, and setters
        
        public String getDescription() {
            return type + " (" + horsepower + " HP)";
        }
    }
}
```
