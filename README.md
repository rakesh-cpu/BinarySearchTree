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
        System.out.println("your trying enter already exicited element:");
    }
    return root;

}
public void search(node root,int key){
     node current=root;
      boolean found=false;
      while(found==false && current!=null){
          
          if(current.data==key){
              
              found=true;
          }
          else if(key<current.data){
              current.lst=current;
          }
          else if(key>current.data){
              current.rst=current;
          }
         
      }
      if(found==true){
          System.out.print("element found"+current.data);
      }
      else{
          System.out.print("element not found");
      }
      

}
public void delete(node root,int key){
      node head=root;
      node parent=root;
      node current=root;
      boolean found=false;
      while(!found && current!=null){
          if(current.data==key){
              
              found=true;
          }
          else if(key<current.data){
              current.lst=current;
          }
          else if(key>current.data){
              current.rst=current;
          }
      }
      
      
    
}
public static void inorder(node root){
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
    int arr[]={500,400,700,300,480,470,475,490,650,800,780};
    int size=arr.length;
    for(int i=0;i<size;i++){
       root=tree.insert(root,arr[i]);
    }
    tree.inorder(root);
    System.out.println("enter key :");
    int key=sc.nextInt();
    
    tree.search(root,key);
    //tree.delete(root,key);
    
    
}    
}
