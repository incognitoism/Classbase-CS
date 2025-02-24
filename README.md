// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MatrixOperations {
    
    uint8 public size;
    int8[][] private A;
    int8[][] private B;
    uint private nonce;

    // Constructor to initialize matrix size and generate random matrices
    constructor(uint8 _size) {
        require(_size > 0, "Matrix size must be greater than 0");
        size = _size;
        
        // Initialize matrices
        for (uint8 i = 0; i < size; i++) {
            A.push(new int8[](size));
            B.push(new int8[](size));
            for (uint8 j = 0; j < size; j++) {
                A[i][j] = randomNumber(i, j);
                B[i][j] = randomNumber(i + 1, j + 1);
            }
        }
    }

    // Function to generate pseudo-random numbers (between 1 and 10)
    function randomNumber(uint8 i, uint8 j) private returns (int8) {
        nonce++;
        return int8(uint8(uint256(keccak256(abi.encodePacked(block.timestamp, msg.sender, nonce, i, j)))) % 10 + 1);
    }

    // Function to get matrices
    function getMatrices() public view returns (int8[][] memory, int8[][] memory) {
        return (A, B);
    }

    // Function to add two matrices
    function addMatrices() public view returns (int8[][] memory) {
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
    function subtractMatrices() public view returns (int8[][] memory) {
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
    function multiplyMatrices() public view returns (int8[][] memory) {
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