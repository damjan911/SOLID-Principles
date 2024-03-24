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
 
