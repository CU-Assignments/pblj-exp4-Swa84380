import java.util.*;

class Employee {
    int id;
    String name;
    double salary;

    Employee(int id, String name, double salary) {
        this.id = id;
        this.name = name;
        this.salary = salary;
    }

    @Override
    public String toString() {
        return "ID: " + id + ", Name: " + name + ", Salary: " + salary;
    }
}

public class EmployeeManagement {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        ArrayList<Employee> employees = new ArrayList<>();

        while (true) {
            System.out.println("1. Add Employee");
            System.out.println("2. Update Employee");
            System.out.println("3. Remove Employee");
            System.out.println("4. Search Employee");
            System.out.println("5. Show All Employees");
            System.out.println("6. Exit");
            System.out.print("Enter choice: ");
            int choice = sc.nextInt();
            sc.nextLine(); // Consume newline

            if (choice == 1) {
                System.out.print("Enter ID: ");
                int id = sc.nextInt();
                sc.nextLine(); // Consume newline
                System.out.print("Enter Name: ");
                String name = sc.nextLine();
                System.out.print("Enter Salary: ");
                double salary = sc.nextDouble();
                employees.add(new Employee(id, name, salary));

            } else if (choice == 2) {
                System.out.print("Enter ID to update: ");
                int id = sc.nextInt();
                Employee emp = null;
                for (Employee e : employees) {
                    if (e.id == id) {
                        emp = e;
                        break;
                    }
                }
                if (emp != null) {
                    sc.nextLine(); // Consume newline
                    System.out.print("Enter new Name: ");
                    emp.name = sc.nextLine();
                    System.out.print("Enter new Salary: ");
                    emp.salary = sc.nextDouble();
                } else {
                    System.out.println("Employee not found!");
                }

            } else if (choice == 3) {
                System.out.print("Enter ID to remove: ");
                int id = sc.nextInt();
                employees.removeIf(e -> e.id == id);

            } else if (choice == 4) {
                System.out.print("Enter ID to search: ");
                int id = sc.nextInt();
                boolean found = false;
                for (Employee e : employees) {
                    if (e.id == id) {
                        System.out.println(e);
                        found = true;
                        break;
                    }
                }
                if (!found) {
                    System.out.println("Employee not found!");
                }

            } else if (choice == 5) {
                for (Employee e : employees) {
                    System.out.println(e);
                }

            } else if (choice == 6) {
                break;
            } else {
                System.out.println("Invalid choice! Try again.");
            }
        }
        sc.close();
    }
}
