# クラス設計書（自動生成想定）

> このファイルは自動生成想定。手動編集禁止。

## Employee
- id: long
- firstName: String
- lastName: String
- email: String

## EmployeeService
- getAllEmployees(): List<Employee>
- saveEmployee(Employee employee): void
- getEmployeeById(long id): Employee
- deleteEmployeeById(long id): void
- findPaginated(int pageNo, int pageSize, String sortField, String sortDirection): Page<Employee>

## EmployeeRepository
- findAll(): List<Employee>
- findAll(Pageable pageable): Page<Employee>
- findById(Long id): Optional<Employee>
- save(Employee employee): Employee
- deleteById(Long id): void

## EmployeeController
- viewHomePage(Model model): String
- showNewEmployeeForm(Model model): String
- saveEmployee(Employee employee): String
- showFormForUpdate(long id, Model model): String
- deleteEmployee(long id): String
- findPaginated(int pageNo, String sortField, String sortDir, Model model): String
