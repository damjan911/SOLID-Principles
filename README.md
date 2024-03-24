# SOLID-Principles

### SOLID Principles are the Design Principles that enable us to manage several Software Design Problems, which they must be followed to develop flexible, maintainable and scalable Software Systems. Each principle focuses on a specific aspect of Software Design.
### SOLID is an acronym for the following:<br>
   - [S: Single Responsibility Principle (SRP)](#features)
   - [O: Open-closed Principle (OCP)](#features)
   - [L: Liskov substitution Principle (LSP)](#features)
   - [I: Interface Segregation Principle (ISP)](#features)
   - [D: Dependency Inversion Principle (DIP)](#features)


# Single Responsibility Principle (SRP)

### This principle states that a class should have only one reason to change, meaning it should have only one responsibility or job.

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
     
 

 
