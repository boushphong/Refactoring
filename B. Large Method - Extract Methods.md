# Large Method

## BAD CODE
**Why:**
- Large methods make code harder to read and harder to unit test
```java
class Vehicle {
    private String make;
    private String model;
    private int year;
    private String color;
    private int mileage;
    
    // Constructors, getters, and setters
    
    public void printInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
        System.out.println("Color: " + color);
        System.out.println("Mileage: " + mileage);
        
        // Additional logic and operations specific to printing vehicle information ...
    }
}
```

# Extract Methods - Refactoring Technique

## GOOD CODE
**Why:**
- Easier to read and unit tests (NOTE: Extracting print methods might not be a realistic refactoring example)
```java
public class Vehicle {
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
