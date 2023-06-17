# Complex Conditional

## BAD CODE
**Why:**
- Complex condition makes the code hard to read
```java
class Vehicle {
    private int year;
    private double price;

    // Constructors, getters, and setters
    
    // Complex Condition - If the conditions are long, and there many conditions, it would be hard to read
    public void printTaxInformation() {
        if (year < 2010 && price > 20000) {
            double tax = price * 0.1;
            System.out.println("Tax to be paid: " + tax);
        } else {
            System.out.println("No tax to be paid.");
        }
    }
}

```

# Explainatory Variable - Refactoring Technique

## GOOD CODE
**Why:**
- Simplify the condition with an explainatory variable. This won't force the readers to focus on the details.
```java
class Vehicle {
    private int year;
    private double price;

    // Constructors, getters, and setters
    
    public void printTaxInformation() {
        boolean isTaxApplicable = year < 2010 && price > 20000; // Explainatory Variable
        
        if (isTaxApplicable) {
            double tax = price * 0.1;
            System.out.println("Tax to be paid: " + tax);
        } else {
            System.out.println("No tax to be paid.");
        }
    }
}
```
