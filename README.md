// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

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

    function calculateBonus() public view returns (uint) {
        return (salary * 10) / 100;
    }
}

contract Manager is Employee {
    uint public numberOfProjects;

    constructor(string memory _name, string memory _address, uint _salary, uint _numProjects)
        Employee(_name, _address, _salary, "Manager")
    {
        numberOfProjects = _numProjects;
    }

    function manageProject() public view returns (string memory) {
        return "Managing multiple projects.";
    }
}

contract Developer is Employee {
    string public programmingLanguage;

    constructor(string memory _name, string memory _address, uint _salary, string memory _language)
        Employee(_name, _address, _salary, "Developer")
    {
        programmingLanguage = _language;
    }

    function generateReport() public view returns (string memory) {
        return "Generating developer performance report.";
    }
}

contract Programmer is Employee {
    string public favoriteIDE;

    constructor(string memory _name, string memory _address, uint _salary, string memory _ide)
        Employee(_name, _address, _salary, "Programmer")
    {
        favoriteIDE = _ide;
    }

    function manageCode() public view returns (string memory) {
        return "Managing and optimizing the codebase.";
    }
}