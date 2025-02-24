// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MatrixOperations {
    
    // Hardcoded 2x2 matrices
    int8[2][2] private A = [[1, 2], [3, 4]];
    int8[2][2] private B = [[5, 6], [7, 8]];

    // Function to add two matrices
    function addMatrices() public view returns (int8[2][2] memory) {
        int8[2][2] memory result;
        for (uint8 i = 0; i < 2; i++) {
            for (uint8 j = 0; j < 2; j++) {
                result[i][j] = A[i][j] + B[i][j];
            }
        }
        return result;
    }

    // Function to subtract two matrices
    function subtractMatrices() public view returns (int8[2][2] memory) {
        int8[2][2] memory result;
        for (uint8 i = 0; i < 2; i++) {
            for (uint8 j = 0; j < 2; j++) {
                result[i][j] = A[i][j] - B[i][j];
            }
        }
        return result;
    }

    // Function to multiply two matrices
    function multiplyMatrices() public view returns (int8[2][2] memory) {
        int8[2][2] memory result;
        for (uint8 i = 0; i < 2; i++) {
            for (uint8 j = 0; j < 2; j++) {
                result[i][j] = 0;
                for (uint8 k = 0; k < 2; k++) {
                    result[i][j] += A[i][k] * B[k][j];
                }
            }
        }
        return result;
    }
}