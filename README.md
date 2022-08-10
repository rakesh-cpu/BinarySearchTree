# BinarySearchTree
//operations on binarysearchtree
import java.util.*;
public class BST{
    
    public static class node{
        int data;
        node lst;
        node rst;
             node(int info){
                 data=info;
                 lst=null;
                 rst=null;
                 
             }   
    }
    public  node  insert(node root,int element){
        if(root==null){
          root = new node(element);
            root.data=element;
            return root;
        }
        else if(element <root.data){
            root.lst=insert(root.lst,element);
            
        }
        else if(element >root.data){
            root.rst=insert(root.rst,element);
        }
        else{
            System.out.println("trying enter already exicited element:");
        }
        return root;
    
    }
    public void inorder(node root){
        if(root==null){
            return;
        }
        inorder(root.lst);
        
        System.out.print(root.data+" ");

        
        inorder(root.rst);
        
    }
    public static void main(String args[]){
        BST  tree = new BST();
        node root=null;
        Scanner sc = new Scanner(System.in);
        int arr[]={40,6,71,1,51,100};
        int size=arr.length;
        for(int i=0;i<size;i++){
           root=tree.insert(root,arr[i]);
        }
        tree.inorder(root);
        
        
    }    
}
