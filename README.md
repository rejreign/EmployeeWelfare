# EmployeeWelfare
Given the following JavaScript functions:

# What is the pay grade of the employee with a Salary of X = 75000?
# How much in tax will an employee with a Salary of X = 25000 pay?
# What is the bonus paid for an employee with a Salary of X = 45000?
# What are the benefits for employees with a Salary between X = 60000 and 70000
# What cadre does an employee with a Salary of X = 10000 belong?

let Employee = {
  salary: 45000
};

let payGrades = {
  entryLevel: { taxMultiplier: .05, benefits: ['health'], minSalary: 25000, maxSalary: 49999 },
  midLevel: { taxMultiplier: .1, benefits: ['health', 'housing'], minSalary: 50000, maxSalary: 99999 },
  seniorLevel: { taxMultiplier: .2, benefits: ['health', 'housing', 'wellness', 'gym'], minSalary: 100000, maxSalary: 200000 }
};

function calculateTax() {
  return payGrades[getCadre()].taxMultiplier * Employee.salary;
}

function getBenefits() {
  return payGrades[getCadre()].benefits.join(', ');
}

function calculateBonus() {
  return .02 * Employee.salary;
}

function getCadre() {
  if (Employee.salary >= payGrades.entryLevel.minSalary && Employee.salary <= payGrades.entryLevel.maxSalary) {
    return 'entryLevel';
  } else if (Employee.salary >= payGrades.midLevel.minSalary && Employee.salary <= payGrades.midLevel.maxSalary) {
    return 'midLevel';
  } else return 'seniorLevel';
}

