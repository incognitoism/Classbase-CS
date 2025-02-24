// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MatrixOperations {
    
    // Function to add two matrices
    function addMatrices(int[][] memory A, int[][] memory B) public pure returns (int[][] memory) {
        require(A.length == B.length && A[0].length == B[0].length, "Matrices must have the same dimensions");

        uint rows = A.length;
        uint cols = A[0].length;
        int[][] memory result = new int[][](rows);

        for (uint i = 0; i < rows; i++) {
            result[i] = new int[](cols);
            for (uint j = 0; j < cols; j++) {
                result[i][j] = A[i][j] + B[i][j];
            }
        }
        return result;
    }

    // Function to subtract two matrices
    function subtractMatrices(int[][] memory A, int[][] memory B) public pure returns (int[][] memory) {
        require(A.length == B.length && A[0].length == B[0].length, "Matrices must have the same dimensions");

        uint rows = A.length;
        uint cols = A[0].length;
        int[][] memory result = new int[][](rows);

        for (uint i = 0; i < rows; i++) {
            result[i] = new int[](cols);
            for (uint j = 0; j < cols; j++) {
                result[i][j] = A[i][j] - B[i][j];
            }
        }
        return result;
    }

    // Function to multiply two matrices
    function multiplyMatrices(int[][] memory A, int[][] memory B) public pure returns (int[][] memory) {
        require(A[0].length == B.length, "Invalid matrix dimensions for multiplication");

        uint rows = A.length;
        uint cols = B[0].length;
        uint common = A[0].length;
        int[][] memory result = new int[][](rows);

        for (uint i = 0; i < rows; i++) {
            result[i] = new int[](cols);
            for (uint j = 0; j < cols; j++) {
                int sum = 0;
                for (uint k = 0; k < common; k++) {
                    sum += A[i][k] * B[k][j];
                }
                result[i][j] = sum;
            }
        }
        return result;
    }
}