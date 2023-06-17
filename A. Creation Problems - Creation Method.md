# Creation Problem

## BAD CODE
**Why:**
- More constructors, more problems
- Constructors can't have the same attribute signatures
```java
class Vehicle {
    private String make;
    private String model;
    private int year;
    private String plateNumber;

    public Vehicle(String make, String model) {
        this.make = make;
        this.model = model;
    }
  
    //    This however is not possible since there is an attribute signatures conflict.
    //    Both constructors receive 1st and 2nd params as String
    //    public Vehicle(String make, String plateNumber) {
    //        this.make = make;
    //        this.model = plateNumber;
    //    }

    public Vehicle(String make, String model, String plateNumber) {
        this.make = make;
        this.model = model;
        this.plateNumber = plateNumber;
    }
}

public class Main {
    public static void main(String[] args) {
        System.out.println("Hello world!");
        Vehicle unidentifiedCar = new Vehicle("Ferrari", "Scuderia");
        Vehicle identifiedCar = new Vehicle("Ferrari", "Scuderia", "H12-12345");
    }
}
```

# Creation Method - Refactoring Technique

## GOOD CODE
**Why:**
- General purpose constructors are more flexible
```java
class Vehicle {
    private String make;
    private String model;
    private int year;
    private String plateNumber;

    private Vehicle(Builder builder) {
        this.make = builder.make;
        this.model = builder.model;
        this.year = builder.year;
        this.plateNumber = builder.plateNumber;
    }

    public void printInfo() {
        System.out.println("Make: " + make);
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
        System.out.println("Color: " + plateNumber);
    }

    // Getters (Only Getters)

    public static class Builder {
        private String make;
        private String model;
        private int year;
        private String plateNumber;

        public Builder make(String make) {
            this.make = make;
            return this;
        }

        public Builder model(String model) {
            this.model = model;
            return this;
        }

        public Builder year(int year) {
            this.year = year;
            return this;
        }

        public Builder plateNumber(String plateNumber) {
            this.plateNumber = plateNumber;
            return this;
        }

        public Vehicle build() {
            return new Vehicle(this);
        }
    }
}


public class Main {
    public static void main(String[] args) {
        Vehicle car1 = new Vehicle.Builder()
            .make("Toyota")
            .model("Camry")
            .build();

        car1.printInfo();

        //  Make: Toyota
        //  Model: Camry
        //  Year: 0
        //  Color: null

        Vehicle car2 = new Vehicle.Builder()
            .make("Honda")
            .model("Accord")
            .year(2020)
            .plateNumber("H12 - 12345")
            .build();
        
        car2.printInfo();

        //  Make: Honda
        //  Model: Accord
        //  Year: 2020
        //  Color: H12 - 12345
    }
}
```

**NOTE:** You could also use the Factory Method design pattern as an alternative option to avoid overloading too many constructors into a class.
