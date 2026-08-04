# Binary_Tree_Paths
https://leetcode.com/problems/binary-tree-paths

O DFS é o algoritmo ideal para esse caso, uma vez que ele lista todos os caminhos da raiz até a folha e só retrocede quando um caminho é finalizado. A única alteração nesse caso é utilizar um StringBuilder para diminuir a quantidade de Strings instanciadas. Assim que um nó é totalmente processado, o seu valor é removido do StringBuilder para que o próximo caminho não o utilize.
```Java
class Solution { 
    private void buildAllPaths(TreeNode root, StringBuilder currentPath, List<String> paths){
        if(root == null) return;
        int size = currentPath.length();
        if(root.left == null && root.right == null){
            currentPath.append(root.val);
            paths.add(currentPath.toString());
        }else{
            currentPath.append(root.val);
            currentPath.append("->");            
            buildAllPaths(root.left, currentPath, paths);
            buildAllPaths(root.right, currentPath, paths);
        }    
        currentPath.setLength(size);
    }

    public List<String> binaryTreePaths(TreeNode root) {    
        List<String> paths = new ArrayList<>();
        StringBuilder currentPath = new StringBuilder();
        buildAllPaths(root, currentPath, paths);
        return paths;
    }
}
```