# Sudoku-Solver
public class SudokuSolver {
   public static boolean isSafe(int sudoku[][] , int r, int c , int digit){
   // column
   for(int i = 0 ; i<9 ; i++){
    if(digit == sudoku[i][c]){
        return false;
    }
   }
   //row
   for(int j = 0 ; j<9 ; j++){
    if(digit == sudoku[r][j]){
        return false;
    }
   }
   //grid
   int sr = (r/3)*3;
   int sc = (c/3)*3;
   for(int i = sr ; i<sr+3 ; i++ ){
    for(int j = sc ; j<sc+3 ; j++){
        if(sudoku[i][j] == digit){
            return false;
        }
    }
   }
   return true;
  }
  public static void print(int sudoku[][]){
    for(int i = 0 ; i<9 ; i++){
        for(int j = 0 ; j<9 ; j++){
            System.out.print(sudoku[i][j] + " ");
        }
        System.out.println();
    }
  }
   public static boolean sudokuSolver(int sudoku[][] , int r, int c){
   //base
   if(r == 9){
    return true;
   }
   //recursion
    int nextRow = r;
    int nextCol = c+1;
    if(c+1 == 9){
       nextRow = r+1;
       nextCol = 0;
   }
   if(sudoku[r][c] != 0){
    return sudokuSolver(sudoku, nextRow, nextCol);
   }
   for(int i = 1 ; i<=9 ; i++){
    if(isSafe(sudoku,r,c,i)){
        sudoku[r][c] = i;
        if(sudokuSolver(sudoku,nextRow,nextCol)){
        return true;}
    }
    sudoku[r][c] = 0;
   }
   return false;
}
 
 
    public static void main(String [] args){
    int sudoku[][] = {{0,0,8,0,0,0,0,0,0},{4,9,0,1,5,7,0,0,2},{0,0,3,0,0,4,1,9,0},{1,8,5,0,6,0,0,2,0},{0,0,0,0,2,0,0,6,0},{9,6,0,4,0,5,3,0,0},
                         {0,3,0,0,7,2,0,0,4},{0,4,9,0,3,0,0,5,7},{8,2,7,0,0,9,0,1,3}};
    if(sudokuSolver(sudoku,0,0)){
        print(sudoku);
        //System.out.println("vishu");
    }


 }   
}
