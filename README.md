# COC-project-sudoku-Grid-Validator
This program validates a completed 9x9 Sudoku grid by checking: 
1. Each row has digits 1–9 exactly once.
 2. Each column has digits 1–9 exactly once.
 3. Each 3x3 subgrid has digits 1–9 exactly once.
#include <stdio.h>

#define SIZE 9

// Function prototypes
int check_rows(int grid[SIZE][SIZE]);
int check_columns(int grid[SIZE][SIZE]);
int check_subgrids(int grid[SIZE][SIZE]);

int main() {
    // Hard-coded Sudoku grid for validation
    int grid[SIZE][SIZE] = {
        {5,3,4,6,7,8,9,1,2},
        {6,7,2,1,9,5,3,4,8},
        {1,9,8,3,4,2,5,6,7},
        {8,5,9,7,6,1,4,2,3},
        {4,2,6,8,5,3,7,9,1},
        {7,1,3,9,2,4,8,5,6},
        {9,6,1,5,3,7,2,8,4},
        {2,8,7,4,1,9,6,3,5},
        {3,4,5,2,8,6,1,7,9}
    };

    // Run validation checks
    int rows_valid = check_rows(grid);
    int cols_valid = check_columns(grid);
    int subgrids_valid = check_subgrids(grid);

    // Final result
    if (rows_valid && cols_valid && subgrids_valid)
        printf("VALID SOLUTION\n");
    else
        printf("INVALID SOLUTION\n");

    return 0;
}

// Function to check all rows
int check_rows(int grid[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        int seen[SIZE + 1] = {0};
        for (int j = 0; j < SIZE; j++) {
            int num = grid[i][j];
            if (num < 1 || num > 9 || seen[num])
                return 0;
            seen[num] = 1;
        }
    }
    return 1;
}

// Function to check all columns
int check_columns(int grid[SIZE][SIZE]) {
    for (int j = 0; j < SIZE; j++) {
        int seen[SIZE + 1] = {0};
        for (int i = 0; i < SIZE; i++) {
            int num = grid[i][j];
            if (num < 1 || num > 9 || seen[num])
                return 0;
            seen[num] = 1;
        }
    }
    return 1;
}

// Function to check all 3x3 subgrids
int check_subgrids(int grid[SIZE][SIZE]) {
    for (int row = 0; row < SIZE; row += 3) {
        for (int col = 0; col < SIZE; col += 3) {
            int seen[SIZE + 1] = {0};
            for (int i = row; i < row + 3; i++) {
                for (int j = col; j < col + 3; j++) {
                    int num = grid[i][j];
                    if (num < 1 || num > 9 || seen[num])
                        return 0;
                    seen[num] = 1;
                }
            }
        }
    }
    return 1;
}

Concept used
C Programming:

2D Arrays

Nested Loops

Functions

If-Else Statements

Pointers (grid passed as parameter)


Maths & Logic:

Matrix traversal

Logical validation using checklists




---
How to compile
gcc main.c -o sudoku_validator -lm

Out put example 
VALID SOLUTION

If you alter a number in the grid, it will show:

INVALID SOLUTION
