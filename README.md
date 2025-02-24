// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MatrixOperations {
    
    uint private nonce;

    // Function to generate a random matrix
    function generateRandomMatrix(uint8 size) public returns (int8[][] memory) {
        require(size > 0, "Matrix size must be greater than 0");
        int8[][] memory matrix = new int8[][](size);
        
        for (uint8 i = 0; i < size; i++) {
            matrix[i] = new int8[](size);
            for (uint8 j = 0; j < size; j++) {
                matrix[i][j] = randomNumber(i, j);
            }
        }
        return matrix;
    }

    // Function to generate a pseudo-random number between 1 and 10
    function randomNumber(uint8 i, uint8 j) private returns (int8) {
        nonce++;
        return int8(uint8(uint256(keccak256(abi.encodePacked(block.timestamp, msg.sender, nonce, i, j)))) % 10 + 1);
    }

    // Function to add two matrices
    function addMatrices(int8[][] memory A, int8[][] memory B) public pure returns (int8[][] memory) {
        require(A.length == B.length && A[0].length == B[0].length, "Matrices must have the same dimensions");
        uint8 size = uint8(A.length);
        int8[][] memory result = new int8[][](size);
        
        for (uint8 i = 0; i < size; i++) {
            result[i] = new int8[](size);
            for (uint8 j = 0; j < size; j++) {
                result[i][j] = A[i][j] + B[i][j];
            }
        }
        return result;
    }

    // Function to subtract two matrices
    function subtractMatrices(int8[][] memory A, int8[][] memory B) public pure returns (int8[][] memory) {
        require(A.length == B.length && A[0].length == B[0].length, "Matrices must have the same dimensions");
        uint8 size = uint8(A.length);
        int8[][] memory result = new int8[][](size);
        
        for (uint8 i = 0; i < size; i++) {
            result[i] = new int8[](size);
            for (uint8 j = 0; j < size; j++) {
                result[i][j] = A[i][j] - B[i][j];
            }
        }
        return result;
    }

    // Function to multiply two matrices
    function multiplyMatrices(int8[][] memory A, int8[][] memory B) public pure returns (int8[][] memory) {
        require(A.length == B.length && A[0].length == B[0].length, "Matrices must have the same dimensions");
        uint8 size = uint8(A.length);
        int8[][] memory result = new int8[][](size);
        
        for (uint8 i = 0; i < size; i++) {
            result[i] = new int8[](size);
            for (uint8 j = 0; j < size; j++) {
                result[i][j] = 0;
                for (uint8 k = 0; k < size; k++) {
                    result[i][j] += A[i][k] * B[k][j];
                }
            }
        }
        return result;
    }
}