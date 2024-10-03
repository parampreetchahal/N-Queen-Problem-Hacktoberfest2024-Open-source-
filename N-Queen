import java.util.ArrayList;
import java.util.List;

public class NQueens {

    // Function to solve N-Queens problem
    public List<List<String>> solveNQueens(int n) {
        List<List<String>> solutions = new ArrayList<>();
        char[][] board = new char[n][n];
        
        // Initialize the board with empty spots ('.')
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                board[i][j] = '.';
            }
        }
        
        // Track the positions that are being attacked by queens
        boolean[] cols = new boolean[n];         // Columns attack
        boolean[] diag1 = new boolean[2 * n];    // Diagonal (\) attack
        boolean[] diag2 = new boolean[2 * n];    // Anti-diagonal (/) attack

        // Start backtracking from row 0
        backtrack(0, n, board, solutions, cols, diag1, diag2);
        return solutions;
    }

    // Helper function to perform backtracking
    private void backtrack(int row, int n, char[][] board, List<List<String>> solutions, 
                           boolean[] cols, boolean[] diag1, boolean[] diag2) {
        // If we placed queens on all rows, add this solution to the list
        if (row == n) {
            solutions.add(construct(board));
            return;
        }

        for (int col = 0; col < n; col++) {
            int d1 = row - col + n;  // Index for diagonal (\)
            int d2 = row + col;      // Index for anti-diagonal (/)
            
            // If there's no queen in this column or diagonals, place a queen
            if (!cols[col] && !diag1[d1] && !diag2[d2]) {
                board[row][col] = 'Q';
                cols[col] = true;
                diag1[d1] = true;
                diag2[d2] = true;

                // Recurse to the next row
                backtrack(row + 1, n, board, solutions, cols, diag1, diag2);

                // Backtrack: remove the queen and reset the flags
                board[row][col] = '.';
                cols[col] = false;
                diag1[d1] = false;
                diag2[d2] = false;
            }
        }
    }

    // Helper function to construct the board solution from the char[][] array
    private List<String> construct(char[][] board) {
        List<String> res = new ArrayList<>();
        for (int i = 0; i < board.length; i++) {
            res.add(new String(board[i]));
        }
        return res;
    }

    public static void main(String[] args) {
        NQueens solution = new NQueens();
        int n = 8;  // Example with 8-Queens problem
        List<List<String>> result = solution.solveNQueens(n);
        
        // Print all the solutions
        for (List<String> sol : result) {
            for (String row : sol) {
                System.out.println(row);
            }
            System.out.println();
        }
        System.out.println("Number of solutions: " + result.size());
    }
}
