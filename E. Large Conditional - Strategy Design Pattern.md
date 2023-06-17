# Large Conditional

## BAD CODE
**Why:**
- The `printInfo()` method contains a large conditional statement that checks the `year` of the vehicle and prints a corresponding label. This approach is not scalable and violates the Open-Closed Principle, as any change or addition to the labels would require modifying the existing code.
```java
class Vehicle {
    private String make;
    private String model;
    private int year;

    // Constructors, getters, and setters

    public void printInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);

        if (year <= 2000) {
            System.out.println("Vintage Vehicle");
        } else if (year <= 2010) {
            System.out.println("Classic Vehicle");
        } else {
            System.out.println("Modern Vehicle");
        }
    }
}
```

# Strategy Design Pattern - Refactoring Technique

## GOOD CODE
**Why:**
-  We introduce the `Vehicle` abstract class, Each specific Vehicle type (`VintageVehicle`, `ClassicVehicle`, `ModernVehicle`) extends the class and provides its own implementation for the `getTypeLabel()` method.
-  The refactored code adheres to the Strategy Design Pattern, which replaces the large conditional with polymorphism. It allows for easy addition or modification of vehicle types without modifying the Vehicle class itself. This improves code maintainability, promotes separation of concerns, and follows the Open-Closed Principle by being open for extension and closed for modification.
```java

abstract class Vehicle {
    private String make;
    private String model;
    private int year;

    public Vehicle(String make, String model, int year) {
        this.make = make;
        this.model = model;
        this.year = year;
    }

    public void printInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
        System.out.println("Type: " + getTypeLabel());
    }

    public abstract String getTypeLabel();
}

class VintageVehicle extends Vehicle {
    public VintageVehicle(String make, String model, int year) {
        super(make, model, year);
    }

    public String getTypeLabel() {
        return "Vintage Vehicle";
    }
}

class ClassicVehicle extends Vehicle {
    public ClassicVehicle(String make, String model, int year) {
        super(make, model, year);
    }

    public String getTypeLabel() {
        return "Classic Vehicle";
    }
}

class ModernVehicle extends Vehicle {
    public ModernVehicle(String make, String model, int year) {
        super(make, model, year);
    }

    public String getTypeLabel() {
        return "Modern Vehicle";
    }
}

public class Main {
    public static void main(String[] args) {
        ModernVehicle modernVehicle = new ModernVehicle("Ferrari", "Scuderia", 2022);
        modernVehicle.printInfo();
    }
}
```
