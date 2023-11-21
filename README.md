# Single Responsibility Principle (SRP)

The **`Single Responsibility Principle (SRP)`** states that a class should have only one reason to change, meaning it should have only one responsibility or job. Here's a simple example in C# to illustrate SRP:

Let's say you have a class called **`Employee`** that is responsible for both employee information management and printing employee details. This class violates SRP because it has more than one reason to change - if the format of employee details needs to change, or if the way employee information is stored or retrieved changes, the class would have to be modified for multiple reasons.

Here's the initial code that violates SRP:

```csharp
public class Employee
{
    public string Name { get; set; }
    public string EmployeeId { get; set; }
    public double Salary { get; set; }

    // Constructor
    public Employee(string name, string employeeId, double salary)
    {
        Name = name;
        EmployeeId = employeeId;
        Salary = salary;
    }

    // Method to print employee details
    public void PrintEmployeeDetails()
    {
        Console.WriteLine($"Name: {Name}");
        Console.WriteLine($"Employee ID: {EmployeeId}");
        Console.WriteLine($"Salary: {Salary:C}");
    }
}

```

In this code, the **`Employee`** class is responsible for both representing employee data and printing employee details. To adhere to SRP, you can refactor the code to separate these responsibilities into two classes.

Here's a refactored version:

```csharp
// Employee class responsible for employee data
public class Employee
{
    public string Name { get; set; }
    public string EmployeeId { get; set; }
    public double Salary { get; set; }

    public Employee(string name, string employeeId, double salary)
    {
        Name = name;
        EmployeeId = employeeId;
        Salary = salary;
    }
}

// EmployeePrinter class responsible for printing employee details
public class EmployeePrinter
{
    public void PrintEmployeeDetails(Employee employee)
    {
        Console.WriteLine($"Name: {employee.Name}");
        Console.WriteLine($"Employee ID: {employee.EmployeeId}");
        Console.WriteLine($"Salary: {employee.Salary:C}");
    }
}

```

With this refactoring, the **`Employee`** class is responsible for managing employee data, and the **`EmployeePrinter`** class is responsible for printing employee details. This separation of concerns adheres to the Single Responsibility Principle, making the code easier to maintain and extend in the future. If you need to change how employee details are printed or how employee data is managed, you only need to modify the relevant class.
