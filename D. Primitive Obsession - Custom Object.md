# Primitive Obsession

## BAD CODE
**Why:**
In the above code, the engine-related information (engineType and engineHorsepower) is represented using primitive types (String and int). This is an example of "primitive obsession," where the code relies on primitive types to represent a concept that could benefit from a dedicated custom object.

```java
public class Vehicle {
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
- Easier to read and unit tests (NOTE: Extracting print methods might not be a realistic refactoring example)
```java
class Vehicle {
    private String make;
    private String model;
    private int year;
    private String color;
    private int mileage;
    
    // Constructors, getters, and setters
    
    public void printInfo() {
        printMake();
        printModel();
        printYear();
        printColor();
        printMileage();
        
        // Additional logic and operations specific to printing vehicle information
    }
    
    private void printMake() {
        System.out.println("Make: " + make);
    }
    
    private void printModel() {
        System.out.println("Model: " + model);
    }
    
    private void printYear() {
        System.out.println("Year: " + year);
    }
    
    private void printColor() {
        System.out.println("Color: " + color);
    }
    
    private void printMileage() {
        System.out.println("Mileage: " + mileage);
    }
}
```
