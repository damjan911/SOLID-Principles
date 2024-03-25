# SOLID-Principles

### SOLID Principles are the Design Principles that enable us to manage several Software Design Problems, which they must be followed to develop flexible, maintainable and scalable Software Systems. Each principle focuses on a specific aspect of Software Design.
### SOLID is an acronym for the following:<br>
   - [S: Single Responsibility Principle (SRP)](#features)
   - [O: Open-closed Principle (OCP)](#features)
   - [L: Liskov substitution Principle (LSP)](#features)
   - [I: Interface Segregation Principle (ISP)](#features)
   - [D: Dependency Inversion Principle (DIP)](#features)


# Single Responsibility Principle (SRP)

### <ins>IMPORTANT:</ins> This principle states that a class should have only one reason to change, meaning it should have only one responsibility or job.

### Here is the Single Responsibility Principle (SRP) with examples in C#:

### <ins>Bad Example: </ins>

``` // Violating SRP, because the Class has extra Responsibility.

 public class Employee
 {
     // Own Responsibility
     public int CalculateSalary()
     {
         return 100000;
     }

     // Own Responsibility
     public string GetDepartment()
     {
         return "IT";
     }

     // Extra Responsibility

     public void Save()
     {
        // Save Employee to the DataBase.
     }
 }
     

```

###  Now to apply SRP we can seperate Responsibility into two seperate Classes.
     
### <ins>Good Example: </ins>

```
    public class Employee
    {
       public int CalculateSalary()
       {
           return 100000;
       }

       public string GetDepartment()
       {
           return "IT";
       }
    }

    public class EmployeeRepository
    {
       public void Save()
       {
          // Save Employee to the DataBase.
       }
    }

```
### The advantage of this SOLID Principle (SRT) is, when a Class has only one Responsibility or Job, it becomes easier to change and test. If a Class has more Responsibilities,changing one Responsibility may impact others. 

# Open/Closed Principle (OCP)

### <ins>IMPORTANT:</ins> Open/Closed Principle (OCP) states that software entities (classes, modules, functions, etc.) should be open for extension but closed for modification. In other words, you should be able to extend a class's behavior without modifying its source code.

### Here is the Single Open/Closed Principle (OCP) with examples in C#:

### <ins>Bad Example: </ins>

```
    public enum ShapeType
    {
        Rectangle,
        Circle,
        Triangle
    }
    public class Shape
    {
       // Bad example violating OCP
       public ShapeType ShapeType {get; set;}

       public double CalculateArea ()
       {
             double Width;
             double Height;
             double Radius;

           if(ShapeType == "Rectangle")
           {
              return Width * Height;
           }
           else if(ShapeType == "Circle")
           {
              return Math.PI * Radius * Radius;
           }

           return return 0.5 * Base * Height;
       }
    }

```
### Now to apply OCP we need to utilize Inheritance as one of the fourth pillars of Object-oriented programming Language.

### <ins>Good Example: </ins>

```
   // Example of OCP
   public abstract class Shape
   {
      public abstract double Area();
   }

   public class Rectangle : Shape
   {
      public double Width { get; set; }
      public double Height { get; set; }

      public override double Area()
      {
         return Width * Height;
      }
   }

   public class Circle : Shape
   {
      public double Radius { get; set; }

      public override double Area()
      {
         return Math.PI * Radius * Radius;
      }
   }

   public class Triangle : Shape
   {
      public double Base { get; set; }
      public double Height { get; set; }

      public override double Area()
      {
         return 0.5 * Base * Height;
      }
   }

```
# Liskov Substitution Principle (LSP)

### <ins>IMPORTANT:</ins> The Liskov Substitution Principle (LSP) states that an Object of a child class must be able to replace an Object of the parent Class withouth breaking the Application.

### Here is the Liskov Substitution Principle (LSP) with examples in C#:

### <ins>Bad Example: </ins>

```
    public abstract class Animal
    {
         // Method Declared.
         public abstract void Fly();
    }

    public class Bird : Animal
    {
       public virtual void Fly()
       {
          Console.WriteLine("Bird flying");
       }
    }

    public class Duck : Animal
    {
       public virtual void Fly()
       {
          Console.WriteLine("Duck flying");
       }

     }

     public class Ostrich : Animal
     {
        public virtual void Fly()
        { 
           Console.WriteLine("Ostrich flying");
        }
     }

```

### Now to apply LSP we need to throw an Exception for Ostrich in the Fly Method, because as I said the Ostriches are flightless birds.

### <ins>Good Example: </ins>

```
   // Example of LSP
   public class Bird
   {
       public virtual void Fly()
       {
           Console.WriteLine("Bird flying");
       }
   }

   public class Duck : Bird
   {
       public override void Fly()
       {
          Console.WriteLine("Duck flying");
       }
  }

   public class Ostrich : Bird
   {
      public override void Fly()
      {
         throw new NotImplementedException();
      }
  }


```

# Interface Segregation Principle (ISP)

### <ins>IMPORTANT:</ins> The Interface Segregation Principle (ISP) states that clients should not be forced to depend on interfaces they do not use. 

### <ins>Bad Example: </ins>

```
    public interface IVehicle
    {
        void Drive();

        void Fly();
    }

    public class FlyingCar : IVehicle
    {
        public void Drive()
        {
           Console.WriteLine("Drive Car");
        }

        public void Fly()
        {
           Console.WriteLine("Fly Car");
        }
    }

    public class Car : IVehicle
    {
        public void Drive()
        {
            Console.WriteLine("Drive Car");
        }

        public void Fly()
        {
            throw new NotImplementedException();
        }
    }

```

### Now to apply (ISP) it's better to have many small, specific interfaces than one large.

### <ins>Good Example: </ins>

```
    public interface IDrive
    {
        void Drive();

        void Fly();
    }

    public interface IFly
    {
        void Fly();
    }

    public class Car : IDrive
    {
        public void Drive()
        {
            Console.WriteLine("Drive Car");
        }

    }

    public class FlyingCar : IDrive, IFly
    {
        public void Drive()
        {
           Console.WriteLine("Drive Car");
        }

        public void Fly()
        {
           Console.WriteLine("Fly Car");
        }
    }

```

# Dependency Inversion Principle (DIP)














 
