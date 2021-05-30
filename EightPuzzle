package javaapplication297;
import java.util.*;

public class Search 
{
    Queue <TreeNode> frontierBFS = new LinkedList<>();              //next nodes
    Stack <TreeNode> frontierDFS = new Stack<>();
    LinkedList <TreeNode> explored = new LinkedList<>();            //add to explored
    TreeNode int_state;
    
        public Search(TreeNode intState)
        {
                int_state = intState;
        }
            
        public boolean BFS()
        {
            frontierBFS.add(int_state);
        while( ! ( frontierBFS.isEmpty() ) ){
                TreeNode state = frontierBFS.poll();            
                explored.add(state);                        //add node to explored
                if (state.GoalTest())                       //check if it's the goal
                {
                     System.out.println();
                System.out.println("GOAL IS FOUND!!!!");
                state.DisplayPuzzle();
                System.out.println("---------------------");
                    return true;
                }
                else                                        //expand till we find the goal
                {
                    state.DisplayPuzzle();
                }
                state.ExpandBFS();                              
            
            for (int i = 0; i < state.children.size(); i++) {
                TreeNode child = state.children.get(i);
                    if (!(Contains(explored, child))) {             //check if already explored
                    frontierBFS.add(child);
                    }
                }
            }                
            return false;
        }
        public boolean DFS()
        {
            frontierDFS.add(int_state);
        while( ! ( frontierDFS.isEmpty() ) ){
                TreeNode state = frontierDFS.pop();
                explored.add(state);
                if (state.GoalTest()) {
                     System.out.println();
                System.out.println("GOAL IS FOUND!!!!");
                state.DisplayPuzzle();
                System.out.println("---------------------");
                    return true;
                }
                else{
            state.DisplayPuzzle();
            }
            state.ExpandDFS();
            
            for (int i = 0; i < state.children.size(); i++) {
                TreeNode child = state.children.get(i);
                    if (!(Contains(explored, child))) {
                    frontierDFS.add(child);
                    }
                }
            }                
            return false;
        }
  
        public boolean Contains(LinkedList <TreeNode > explored, TreeNode child)        //check if already explored
        {
        boolean contains = false;
        for (int i = 0; i < explored.size(); i++) {
            if (explored.get(i).IsTheSamePuzzle(child.puzzle)) {
                contains = true;
            }
        }
        return contains;
        }
}
import java.util.*;
public class TreeNode {
    int[]puzzle=new int[9];
    int goal[] = {0, 1, 2, 3, 4, 5, 6, 7, 8};
    int col =3;
    int x=0;
    public LinkedList<TreeNode> children = new LinkedList<>();

    public TreeNode(int p[])                        //parametrized constructor to set puzzle
    {
        this.puzzle = p;
    }

    public void CopyPuzzle(int []a,int []b)         
    {
        for(int i=0;i<(col*col);i++)
        {
            a[i]=b[i];
        }
    }
    
    public boolean IsTheSamePuzzle(int [] ar){      //check if puzzle appeared before
        for (int i = 0; i < ar.length; i++) {
            if (puzzle[i] != ar[i]) {
                return false;
            }
        }
        return true;
    }
    
    public void MoveRight(int []p,int i)
    {
        int pc[]=new int[9];
        if(i%col<2){
        CopyPuzzle(pc, p);
        int temp=pc[i];
        pc[i]=pc[i+1];
        pc[i+1]=temp;
        TreeNode NewTreeChild = new TreeNode(pc);
        children.add(NewTreeChild);
        }
    }
    public void MoveLeft(int []p,int i)
    {
        int pc[]=new int[9];
        if(i%col>0){
        CopyPuzzle(pc, p);
        int temp=pc[i];
        pc[i]=pc[i-1];
        pc[i-1]=temp;
        TreeNode NewTreeChild = new TreeNode(pc);
        children.add(NewTreeChild);
        }
    }
    public void MoveUp(int []p,int i)
    {
        int pc[]=new int[9];
        if(i>2){
        CopyPuzzle(pc, p);
        int temp=pc[i];
        pc[i]=pc[i-3];
        pc[i-3]=temp;
        TreeNode NewTreeChild = new TreeNode(pc);
        children.add(NewTreeChild);
        }
    }
    
    public void MoveDown(int []p,int i)
    {
        int pc[]=new int[9];
        if(i<puzzle.length-col){
        CopyPuzzle(pc, p);
        int temp=pc[i];
        pc[i]=pc[i+3];
        pc[i+3]=temp;
        TreeNode NewTreeChild = new TreeNode(pc);
        children.add(NewTreeChild);
        }
    }
    public boolean GoalTest()               //comparing with the goal
    {
        
        boolean test=true;
        for(int i=0 ; i < 9 ; i++)
        {
            if(goal[i]!=puzzle[i])
            {
                test=false;
            }
        }
        return test;

    }
    public void DisplayPuzzle()             //show puzzle
    {
      System.out.println();
        int index=0;
        for(int i=0;i<3;i++)
        {
            for(int j=0;j<3;j++)
            {
                System.out.print(puzzle[index]+"|");
                index++;
            }
            System.out.println("-------");
        }
    }
    
    public void ExpandBFS()                 //movements of each search
    {
        for(int i=0;i<9;i++)
        {
            if( puzzle[i]==0)
            {
                x=i;
            }
        }
        MoveLeft(puzzle,x);
        MoveRight(puzzle,x);
        MoveUp(puzzle,x);
        MoveDown(puzzle,x);
    }
    
    public void ExpandDFS()
    {
        for(int i=0;i<9;i++)
        {
            if( puzzle[i]==0)
            {
                x=i;
            }
        }
        MoveRight(puzzle,x);
        MoveDown(puzzle,x);
        MoveLeft(puzzle,x);
        MoveUp(puzzle,x);
    }

}
public class JavaApplication297 {

    /**
     * @param args the command line arguments
     */
    public static void main(String[] args) {
        
        int[] puzzle = {1,2,5,3,4,0,6,7,8};         //the initial puzzle
        TreeNode rootNode = new TreeNode(puzzle);
        Search s1 = new Search(rootNode);
        //System.out.println("Using Breadth First Search:");
        //s1.BFS();
        System.out.println("Using Deapth First Search:");
        s1.DFS();
        
    }
    
}
