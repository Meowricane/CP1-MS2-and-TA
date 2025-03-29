
package com.mycompany.motorph;

import java.util.*;
import java.time.*;
import java.time.format.DateTimeFormatter;
import java.time.temporal.ChronoUnit;


class Employee {
    String empNumber, lastName, firstName, birthday, address, phoneNumber, sssNumber, philhealthNumber, tinNumber, pagibigNumber, status, position, supervisor;
    double basicSalary, hourlyRate, sssDeduction;
    
    public Employee(String empNumber, String lastName, String firstName, String birthday, String address, String phoneNumber, String sssNumber, String philhealthNumber, String tinNumber, String pagibigNumber, String status, String position, String supervisor, double basicSalary, double hourlyRate, double sssDeduction) {
        this.empNumber = empNumber;
        this.lastName = lastName;
        this.firstName = firstName;
        this.birthday = birthday;
        this.address = address;
        this.phoneNumber = phoneNumber;
        this.sssNumber = sssNumber;
        this.philhealthNumber = philhealthNumber;
        this.tinNumber = tinNumber;
        this.pagibigNumber = pagibigNumber;
        this.status = status;
        this.position = position;
        this.supervisor = supervisor;
        this.basicSalary = basicSalary;
        this.hourlyRate = hourlyRate;
        this.sssDeduction = sssDeduction;
    }
    
    public void displayEmployeeInfo() {
        System.out.println("Employee Number: " + empNumber);
        System.out.println("Name: " + firstName + " " + lastName);
        System.out.println("Birthday: " + birthday);
        System.out.println("Address: " + address);
        System.out.println("Phone Number: " + phoneNumber);
        System.out.println("SSS #: " + sssNumber);
        System.out.println("PhilHealth #: " + philhealthNumber);
        System.out.println("TIN #: " + tinNumber);
        System.out.println("Pag-IBIG #: " + pagibigNumber);
        System.out.println("Status: " + status);
        System.out.println("Position: " + position);
        System.out.println("Immediate Supervisor: " + supervisor);
        System.out.println("Basic Salary: PHP " + basicSalary);
        System.out.println("Rice Subsidy: PHP " + 1500); // Assuming a fixed value
        System.out.println("Phone Allowance: PHP " + 1000); // Assuming a fixed value
        System.out.println("Clothing Allowance: PHP " + 1000); // Assuming a fixed value
        System.out.println("Gross Semi-Monthly Rate: PHP " + (basicSalary / 2));
        System.out.println("Hourly Rate: PHP " + hourlyRate);
        System.out.println("-----------------------------");
    }
}

class Attendance {
    String empNumber, date, logIn, logOut;
    
    public Attendance(String empNumber, String date, String logIn, String logOut) {
        this.empNumber = empNumber;
        this.date = date;
        this.logIn = logIn;
        this.logOut = logOut;
    }
    
    public double calculateHoursWorked() {
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("H:mm");
        LocalTime logInTime = LocalTime.parse(logIn, formatter);
        LocalTime logOutTime = LocalTime.parse(logOut, formatter);

        if (logInTime.isBefore(LocalTime.of(8, 10))) {
            logInTime = LocalTime.of(8, 0);
        }
        double hoursWorked = ChronoUnit.MINUTES.between(logInTime, logOutTime) / 60.0;
        return Math.round(hoursWorked); // Round to nearest whole number
    }
}

public class MotorPH {
    private static List<Employee> employees = new ArrayList<>();
    private static List<Attendance> attendanceRecords = new ArrayList<>();
    
    public static void main(String[] args) {
        initializeEmployees();
        initializeAttendance();
        displayMenu();
    }
    
    private static void initializeEmployees() {
        employees.add(new Employee("10005", "Hernandez", "Eduard", "09/23/1989", "National Highway, Gingoog, Misamis Occidental", "088-861-012", "918-621-603", "50-5577638-1", "957436191812", "031-702-374-000", "Regular", "IT Operations and Systems", "Lim, Antonio", 52670, 313.51, 1125));
        employees.add(new Employee("10006", "Villanueva", "Andrea Mae", "02/14/1988", "Poblacion, Las Piñas", "918-621-603", "49-1632020-8", "382189453145", "317-674-022-000", "441093369646", "Regular", "HR Manager", "Lim, Antonio", 52670, 313.51, 1125));
        employees.add(new Employee("10007", "San Jose", "Brad", "03/15/1996", "Poblacion, Bislig", "797-009-261", "40-2400714-1", "239192926939", "672-474-690-000", "210850209964", "Regular", "HR Team Leader", "Villanueva, Andrea Mae", 42975, 255.80, 1125));
        employees.add(new Employee("10008", "Romualdez", "Alice", "05/14/1992", "Roxas City", "983-606-799", "55-4476527-2", "545652640232", "888-572-294-000", "211385556888", "Regular", "HR Rank and File", "San Jose, Brad", 22500, 133.93, 1012.50));
        employees.add(new Employee("10009", "Atienza", "Rosie", "09/24/1948", "San Lorenzo", "266-036-427", "41-0644692-3", "708988234853", "604-997-793-000", "260107732354", "Regular", "HR Rank and File", "San Jose, Brad", 22500, 133.93, 1012.50));
    }
    
    private static void initializeAttendance() {
        attendanceRecords.add(new Attendance("10005", "06/03/2024", "9:48", "17:13"));
        attendanceRecords.add(new Attendance("10006", "06/03/2024", "9:31", "19:29"));
        attendanceRecords.add(new Attendance("10007", "06/03/2024", "9:09", "16:30"));
        attendanceRecords.add(new Attendance("10008", "06/03/2024", "9:02", "18:06"));
        attendanceRecords.add(new Attendance("10009", "06/03/2024", "8:18", "17:40"));

        attendanceRecords.add(new Attendance("10005", "06/04/2024", "9:50", "20:20"));
        attendanceRecords.add(new Attendance("10006", "06/04/2024", "10:00", "20:12"));
        attendanceRecords.add(new Attendance("10007", "06/04/2024", "9:16", "16:18"));
        attendanceRecords.add(new Attendance("10008", "06/04/2024", "9:36", "18:56"));
        attendanceRecords.add(new Attendance("10009", "06/04/2024", "10:41", "19:21"));
        attendanceRecords.add(new Attendance("10005", "06/05/2024", "9:10", "17:17"));
        attendanceRecords.add(new Attendance("10006", "06/05/2024", "8:28", "16:52"));
        attendanceRecords.add(new Attendance("10007", "06/05/2024", "9:25", "17:45"));
        attendanceRecords.add(new Attendance("10008", "06/05/2024", "10:44", "18:51"));
        attendanceRecords.add(new Attendance("10009", "06/05/2024", "10:46", "17:54"));
        attendanceRecords.add(new Attendance("10005", "06/06/2024", "10:47", "19:28"));
        attendanceRecords.add(new Attendance("10006", "06/06/2024", "10:11", "17:27"));
        attendanceRecords.add(new Attendance("10007", "06/06/2024", "9:51", "19:58"));
        attendanceRecords.add(new Attendance("10008", "06/06/2024", "9:21", "16:49"));
        attendanceRecords.add(new Attendance("10009", "06/06/2024", "8:47", "17:44"));
        attendanceRecords.add(new Attendance("10005", "06/07/2024", "8:14", "16:58"));
        attendanceRecords.add(new Attendance("10006", "06/07/2024", "8:18", "18:23"));
        attendanceRecords.add(new Attendance("10007", "06/07/2024", "8:12", "15:12"));
        attendanceRecords.add(new Attendance("10008", "06/07/2024", "8:19", "16:22"));
        attendanceRecords.add(new Attendance("10009", "06/07/2024", "10:09", "20:58"));

        attendanceRecords.add(new Attendance("10005", "06/10/2024", "8:05", "18:04"));
        attendanceRecords.add(new Attendance("10006", "06/10/2024", "8:10", "16:39"));
        attendanceRecords.add(new Attendance("10007", "06/10/2024", "10:03", "17:48"));
        attendanceRecords.add(new Attendance("10008", "06/10/2024", "10:06", "19:18"));
        attendanceRecords.add(new Attendance("10009", "06/10/2024", "8:21", "17:52"));

        attendanceRecords.add(new Attendance("10005", "06/11/2024", "8:48", "16:10"));
        attendanceRecords.add(new Attendance("10006", "06/11/2024", "9:26", "18:47"));
        attendanceRecords.add(new Attendance("10007", "06/11/2024", "9:18", "17:50"));
        attendanceRecords.add(new Attendance("10008", "06/11/2024", "8:09", "17:46"));
        attendanceRecords.add(new Attendance("10009", "06/11/2024", "8:28", "18:03"));

        attendanceRecords.add(new Attendance("10005", "06/12/2024", "10:10", "18:34"));
        attendanceRecords.add(new Attendance("10006", "06/12/2024", "9:15", "18:49"));
        attendanceRecords.add(new Attendance("10007", "06/12/2024", "9:01", "16:14"));
        attendanceRecords.add(new Attendance("10008", "06/12/2024", "9:55", "17:36"));
        attendanceRecords.add(new Attendance("10009", "06/12/2024", "10:27", "20:01"));

        attendanceRecords.add(new Attendance("10005", "06/13/2024", "9:56", "18:07"));
        attendanceRecords.add(new Attendance("10006", "06/13/2024", "10:47", "19:54"));
        attendanceRecords.add(new Attendance("10007", "06/13/2024", "10:00", "18:49"));
        attendanceRecords.add(new Attendance("10008", "06/13/2024", "9:14", "19:44"));
        attendanceRecords.add(new Attendance("10009", "06/13/2024", "10:09", "17:16"));

        attendanceRecords.add(new Attendance("10005", "06/14/2024", "8:50", "16:13"));
        attendanceRecords.add(new Attendance("10006", "06/14/2024", "9:36", "16:42"));
        attendanceRecords.add(new Attendance("10007", "06/14/2024", "8:12", "16:15"));
        attendanceRecords.add(new Attendance("10008", "06/14/2024", "8:40", "18:51"));
        attendanceRecords.add(new Attendance("10009", "06/14/2024", "8:16", "18:15"));

    }
    
    private static void displayMenu() {
        Scanner input = new Scanner(System.in);
        while (true) {
            System.out.println("====================================");
            System.out.println("   MotorPH Employee Management   ");
            System.out.println("====================================");
            System.out.println("1. Employee Details");
            System.out.println("2. Attendance Report");
            System.out.println("3. Payroll Computation");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int choice = input.nextInt();
            
            switch (choice) {
                case 1:
                    System.out.print("Enter Employee Number to View: ");
                    String empNum1 = input.next();
                    for (Employee emp : employees) {
                        if (emp.empNumber.equals(empNum1)) {
                            emp.displayEmployeeInfo();
                        }
                    }
                    break;
                case 2:
                    System.out.print("Enter Employee Number to View: ");
                    String empNum2 = input.next();
                    System.out.println("Date       | Log-in | Log-out | Total Work Hours");
                    System.out.println("----------------------------------------------");
                    for (Attendance record : attendanceRecords) {
                        if (record.empNumber.equals(empNum2)) {
                            System.out.printf("%s | %s | %s | %d%n",
                                    record.date, record.logIn, record.logOut, (int) record.calculateHoursWorked());
                        }
                    }
                    break;

                case 3:
                    computePayroll();
                    break;
                case 4:
                    System.out.println("Leaving Employee Portal...");
                    input.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        }
    }
    
    private static double computeSSSDeduction(double salary) {
        double sssDeduction = 0;

        if (salary < 3250) {
            sssDeduction = 135;
        } else if (salary <= 3750) {
            sssDeduction = 157.50;
        } else if (salary <= 4250) {
            sssDeduction = 180;
        } else if (salary <= 4750) {
            sssDeduction = 202.50;
        } else if (salary <= 5250) {
            sssDeduction = 225;
        } else if (salary <= 5750) {
            sssDeduction = 247.50;
        } else if (salary <= 6250) {
            sssDeduction = 270;
        } else if (salary <= 6750) {
            sssDeduction = 292.50;
        } else if (salary <= 7250) {
            sssDeduction = 315;
        } else if (salary <= 7750) {
            sssDeduction = 337.50;
        } else if (salary <= 8250) {
            sssDeduction = 360;
        } else if (salary <= 8750) {
            sssDeduction = 382.50;
        } else if (salary <= 9250) {
            sssDeduction = 405;
        } else if (salary <= 9750) {
            sssDeduction = 427.50;
        } else if (salary <= 10250) {
            sssDeduction = 450;
        } else if (salary <= 10750) {
            sssDeduction = 472.50;
        } else if (salary <= 11250) {
            sssDeduction = 495;
        } else if (salary <= 11750) {
            sssDeduction = 517.50;
        } else if (salary <= 12250) {
            sssDeduction = 540;
        } else if (salary <= 12750) {
            sssDeduction = 562.50;
        } else if (salary <= 13250) {
            sssDeduction = 585;
        } else if (salary <= 13750) {
            sssDeduction = 607.50;
        } else if (salary <= 14250) {
            sssDeduction = 630;
        } else if (salary <= 14750) {
            sssDeduction = 652.50;
        } else if (salary <= 15250) {
            sssDeduction = 675;
        } else if (salary <= 15750) {
            sssDeduction = 697.50;
        } else if (salary <= 16250) {
            sssDeduction = 720;
        } else if (salary <= 16750) {
            sssDeduction = 742.50;
        } else if (salary <= 17250) {
            sssDeduction = 765;
        } else if (salary <= 17750) {
            sssDeduction = 787.50;
        } else if (salary <= 18250) {
            sssDeduction = 810;
        } else if (salary <= 18750) {
            sssDeduction = 832.50;
        } else if (salary <= 19250) {
            sssDeduction = 855;
        } else if (salary <= 19750) {
            sssDeduction = 877.50;
        } else if (salary <= 20250) {
            sssDeduction = 900;
        } else if (salary <= 20750) {
            sssDeduction = 922.50;
        } else if (salary <= 21250) {
            sssDeduction = 945;
        } else if (salary <= 21750) {
            sssDeduction = 967.50;
        } else if (salary <= 22250) {
            sssDeduction = 990;
        } else if (salary <= 22750) {
            sssDeduction = 1012.50;
        } else if (salary <= 23250) {
            sssDeduction = 1035;
        } else if (salary <= 23750) {
            sssDeduction = 1057.50;
        } else if (salary <= 24250) {
            sssDeduction = 1080;
        } else if (salary <= 24750) {
            sssDeduction = 1102.50;
        } else {
            sssDeduction = 1125;
        }

        return sssDeduction / 2;
    }

 

    private static void computePayroll() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter Employee Number to View Payroll: ");
        String enteredEmpNumber = scanner.nextLine();

        boolean found = false;
        for (Employee emp : employees) {
            if (emp.empNumber.equals(enteredEmpNumber)) {
                found = true;
                double totalHours = 0;
                for (Attendance record : attendanceRecords) {
                    if (record.empNumber.equals(emp.empNumber)) {
                        totalHours += record.calculateHoursWorked();
                    }
                }

                double grossSalary = totalHours * emp.hourlyRate;
                double sssDeduction = computeSSSDeduction(emp.basicSalary);

                // Compute PhilHealth Deduction
                double monthlyPremium = emp.basicSalary * 0.03;
                if (monthlyPremium > 1800) {
                    monthlyPremium = 1800;
                }
                double philhealthDeduction = monthlyPremium / 2;

                // Compute Pag-IBIG Deduction
                double pagibigDeduction = (emp.basicSalary <= 1500) ? emp.basicSalary * 0.01 : emp.basicSalary * 0.02;

                // Compute Taxable Income
                double taxableIncome = grossSalary - sssDeduction - philhealthDeduction - pagibigDeduction;

                // Compute Withholding Tax
                double withholdingTax = 0;
                if (taxableIncome > 666667) {
                    withholdingTax = 200833.33 + (taxableIncome - 666667) * 0.35;
                } else if (taxableIncome > 166667) {
                    withholdingTax = 40833.33 + (taxableIncome - 166667) * 0.32;
                } else if (taxableIncome > 66667) {
                    withholdingTax = 10833 + (taxableIncome - 66667) * 0.30;
                } else if (taxableIncome > 33333) {
                    withholdingTax = 2500 + (taxableIncome - 33333) * 0.25;
                } else if (taxableIncome > 20833) {
                    withholdingTax = (taxableIncome - 20833) * 0.20;
                }

                // Round all final values to whole numbers
                long roundedGrossSalary = Math.round(grossSalary);
                long roundedSSSDeduction = Math.round(sssDeduction);
                long roundedPhilHealthDeduction = Math.round(philhealthDeduction);
                long roundedPagibigDeduction = Math.round(pagibigDeduction);
                long roundedWithholdingTax = Math.round(withholdingTax);
                long netSalary = roundedGrossSalary - (roundedSSSDeduction + roundedPhilHealthDeduction + roundedPagibigDeduction + roundedWithholdingTax);

                // Display Payroll Computation
                System.out.println("\n=======================================");
                System.out.println("       Payroll Details for " + emp.firstName + " " + emp.lastName);
                System.out.println("=======================================");
                System.out.printf("Basic Monthly Salary:            PHP %,d%n", Math.round(emp.basicSalary));
                System.out.printf("Semi-Monthly Rate:            PHP %,d%n", roundedGrossSalary);
                System.out.println("---------------------------------------");
                System.out.println("DEDUCTIONS:");
                System.out.printf("SSS Deduction:           PHP %,d%n", roundedSSSDeduction);
                System.out.printf("PhilHealth Deduction:    PHP %,d%n", roundedPhilHealthDeduction);
                System.out.printf("Pag-IBIG Deduction:      PHP %,d%n", roundedPagibigDeduction);
                System.out.printf("Withholding Tax:         PHP %,d%n", roundedWithholdingTax);
                System.out.println("---------------------------------------");
                System.out.printf("Net Salary:              PHP %,d%n", netSalary);
                System.out.println("=======================================");
                break;
            }
        }

        if (!found) {
            System.out.println("Error: Employee Number not found.");
        }
    }
}
