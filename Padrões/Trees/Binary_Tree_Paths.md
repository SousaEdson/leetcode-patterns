# Binary_Tree_Paths
https://leetcode.com/problems/binary-tree-paths

TO-DO: Otimizar. Ao invés de utilizar uma lista encadeada, utilizar o próprio StringBuilder e remover do stringbuilder após um path for descoberto. O truque é salvar o tamanho do stringbuilder no inicio do método e após a conclusão setar esse mesmo tamanho
```Java
class Solution {

    private void buildAllPaths(TreeNode root, LinkedList<Integer> path, List<String> paths){
        if(root == null) return;
        path.add(root.val);
        if(root.left == null && root.right == null){
            boolean first = true;
            StringBuilder sb = new StringBuilder();
            for(Integer num: path) {
                if(!first) sb.append("->");
                sb.append(String.valueOf(num));
                first = false;                
            }
            paths.add(sb.toString());   
            path.removeLast();            
            return;
        }        
        buildAllPaths(root.left, path, paths);
        buildAllPaths(root.right, path, paths);    
        path.removeLast();    
    }

    public List<String> binaryTreePaths(TreeNode root) {
        List<String> paths = new ArrayList<>();
        buildAllPaths(root, new LinkedList<>(), paths);
        return paths;
    }
}
```