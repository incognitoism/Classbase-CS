// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MatrixOperations {
    
    // Hardcoded matrices
    int8 constant A00 = 1; int8 constant A01 = 2;
    int8 constant A10 = 3; int8 constant A11 = 4;

    int8 constant B00 = 5; int8 constant B01 = 6;
    int8 constant B10 = 7; int8 constant B11 = 8;

    // Function to add two matrices
    function addMatrices() public pure returns (int8[2][2] memory) {
        return [
            [A00 + B00, A01 + B01],
            [A10 + B10, A11 + B11]
        ];
    }

    // Function to subtract two matrices
    function subtractMatrices() public pure returns (int8[2][2] memory) {
        return [
            [A00 - B00, A01 - B01],
            [A10 - B10, A11 - B11]
        ];
    }

    // Function to multiply two matrices
    function multiplyMatrices() public pure returns (int8[2][2] memory) {
        return [
            [
                A00 * B00 + A01 * B10, 
                A00 * B01 + A01 * B11
            ],
            [
                A10 * B00 + A11 * B10, 
                A10 * B01 + A11 * B11
            ]
        ];
    }
}