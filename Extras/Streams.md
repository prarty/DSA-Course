## Problems:


1. Write a program to print employee details working in each department
2. Write a program to print employees count working in each department
3. Write a program to print active and inactive employees in the given collection
4. Write a program to print Max/Min employee salary from the given collection
5. Write a program to print the max salary of an employee from each department

## Solutions
``
Consider Employee List :  employees
``

Write a program to print employee details working in each department

````
Map<Integer, List<Employee>> employeePerDepartment = employees
                                                    .stream()
                                                    .collect(Collectors
                                                             .groupingBy(Employee::getDepartmentId, Collectors.toList()
                                                             );

employeePerDepartment
.entrySet()
.forEach(entry -> System.out.println("Dep Id = "+entry.getKey()+" Employee= "+entry.getValue());
````

Write a program to print employees count working in each department
````

Map<Integer, Long> countMap = employee
                              .stream()
                              .collect(Collectors
                                       .groupingBy(Employee::getDepId, Collectors.counting()
                                       );

countMap
.entrySet()
.forEach(entry -> System.out.println("dep Id= "+entry.getKey()+" count= "+entry.getValue());
````

Write a program to print active and inactive employees in the given collection
````

employee
.stream()
.filter(e -> "Active".equals(e.getStatus))
.forEach(e -> System.out.println(e));

Or

Long count = employee
            .stream()
            .filter(e -> "Inactive".equals(e.getStatus))
            .count();
````

Write a program to print Max/Min employee salary from the given collection
````

Optional<Employee> maxSalEmp = employee
                               .stream()
                               .max(Comparator.comparing(Employee::getSalary));

Optional<Employee> minSalEmp = employees
                               .stream()
                               .min(Comparator.comparing(Employee::getSalary));
````

Write a program to print the max salary of an employee from each department
````
Map<Integer, Optional<Employee>> resMap = employees
                                          .stream()
                                          .collect(Collectors
                                                   .groupingBy(Employee::getDepId, Collectors.reducing(
                                                                                   BinaryOperator.maxBy(Comparator.comparing(Employee::getSalary))
                                                                                   )
);