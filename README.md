
Here is the Solidity code for the first assignment, implementing a contract hierarchy for employees in a company:

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

// Base contract for Employee
contract Employee {
    string public name;
    string public addressDetails;
    uint public salary;
    string public jobTitle;

    constructor(string memory _name, string memory _address, uint _salary, string memory _jobTitle) {
        name = _name;
        addressDetails = _address;
        salary = _salary;
        jobTitle = _jobTitle;
    }

    // Function to calculate bonuses (example: 10% of salary)
    function calculateBonus() public view returns (uint) {
        return (salary * 10) / 100;
    }
}

// Derived contract for Manager
contract Manager is Employee {
    uint public numberOfProjects;

    constructor(string memory _name, string memory _address, uint _salary, uint _numProjects)
        Employee(_name, _address, _salary, "Manager")
    {
        numberOfProjects = _numProjects;
    }

    // Function to manage projects
    function manageProject() public view returns (string memory) {
        return "Managing multiple projects.";
    }
}

// Derived contract for Developer
contract Developer is Employee {
    string public programmingLanguage;

    constructor(string memory _name, string memory _address, uint _salary, string memory _language)
        Employee(_name, _address, _salary, "Developer")
    {
        programmingLanguage = _language;
    }

    // Function to generate performance reports
    function generateReport() public view returns (string memory) {
        return "Generating developer performance report.";
    }
}

// Derived contract for Programmer
contract Programmer is Employee {
    string public favoriteIDE;

    constructor(string memory _name, string memory _address, uint _salary, string memory _ide)
        Employee(_name, _address, _salary, "Programmer")
    {
        favoriteIDE = _ide;
    }

    // Function to manage codebase
    function manageCode() public view returns (string memory) {
        return "Managing and optimizing the codebase.";
    }
}

Explanation:

1. Base Contract: Employee

Stores employee details like name, address, salary, and job title.

Implements a calculateBonus function that calculates a 10% bonus.



2. Derived Contracts:

Manager: Inherits from Employee and adds numberOfProjects, along with a function to manage projects.

Developer: Inherits from Employee and adds programmingLanguage, along with a function to generate reports.

Programmer: Inherits from Employee and adds favoriteIDE, along with a function to manage the codebase.




This structure effectively demonstrates inheritance and constructor usage in Solidity. Let me know if you need any modifications!

