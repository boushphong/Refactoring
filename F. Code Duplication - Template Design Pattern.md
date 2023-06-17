# Code Duplication

## BAD CODE
**Why:**
- The `start()` and `stop()` methods contain code that is duplicated across different types of vehicles. This duplication violates the DRY (Don't Repeat Yourself) principle and makes maintenance and future enhancements more challenging.


```java
class Car {
    private String make;
    private String model;
    private int year;
    
    // Constructors, getters, and setters
    
    public void start() {
        // Code to start a vehicle
        System.out.println("Starting the vehicle...");
        // Code specific to starting a car
        System.out.println("Ignition sequence initiated for Car.");
        // Common code for all vehicles
        System.out.println("Vehicle engine started.");
    }
    
    public void stop() {
        // Code to stop a vehicle
        System.out.println("Stopping the vehicle...");
        // Code specific to stopping a car
        System.out.println("Applying brakes for Car.");
        // Common code for all vehicles
        System.out.println("Vehicle engine stopped.");
    }
}

class Truck {
    private String make;
    private String model;
    private int year;
    
    // Constructors, getters, and setters
    
    public void start() {
        // Code to start a vehicle
        System.out.println("Starting the vehicle...");
        // Code specific to starting a truck
        System.out.println("Ignition sequence initiated for Truck.");
        // Common code for all vehicles
        System.out.println("Vehicle engine started.");
    }
    
    public void stop() {
        // Code to stop a vehicle
        System.out.println("Stopping the vehicle...");
        // Code specific to stopping a Truck
        System.out.println("Applying brakes for Truck.");
        // Common code for all vehicles
        System.out.println("Vehicle engine stopped.");
    }
}
```

# Template Design Pattern - Refactoring Technique

## GOOD CODE
**Why:**
- The refactored code eliminates code duplication by providing a common template for the `start` and `stop` methods in the `Vehicle` class. Each specific vehicle type only needs to implement its own behavior, resulting in cleaner and more maintainable code.
- The Template Method Design Pattern promotes code reuse, improves readability, and allows for easy extension and modification of the algorithm without modifying the core structure. It eliminates the need for duplicated code and ensures a consistent execution flow across different vehicle types.
```java
abstract class Vehicle {
    private String make;
    private String model;
    private int year;
    
    // Constructors, getters, and setters
    
    public final void start() {
        System.out.println("Starting the vehicle...");
        specificStart();
        commonStart();
    }
    
    public final void stop() {
        System.out.println("Stopping the vehicle...");
        specificStop();
        commonStop();
    }
    
    protected abstract void specificStart();
    
    protected abstract void specificStop();
    
    private void commonStart() {
        System.out.println("Vehicle engine started.");
    }
    
    private void commonStop() {
        System.out.println("Vehicle engine stopped.");
    }
}

class Car extends Vehicle {
    @Override
    protected void specificStart() {
        System.out.println("Ignition sequence initiated for Car.");
    }
    
    @Override
    protected void specificStop() {
        System.out.println("Applying brakes for Car.");
    }
}

class Truck extends Vehicle {
    @Override
    protected void specificStart() {
        System.out.println("Ignition sequence initiated for Truck.");
    }
    
    @Override
    protected void specificStop() {
        System.out.println("Applying brakes for Truck.");
    }
}
```
