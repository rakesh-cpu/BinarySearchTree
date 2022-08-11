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
         node(){
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
public node search(node root,int key){
     node current=root;
      boolean found=false;
      while(found!=true && current!=null){
          
          if(current.data==key){
              
              found=true;
          }
          else if(key<current.data){
              current=current.lst;
          }
          else if(key>current.data){
              current=current.rst;
          }
         
      }
      if(found){
          System.out.println("element found"+current.data);
      }
      else{
          System.out.println("element not found");
      }
     return current; 
      

}
public node delete(node root,int key){
    
      node head=new node();
      head.lst=root;
      node parent=head;
      node current=root;
      boolean found=false;
      while(found!=true && current!=null){
          if(current.data==key){
              
              found=true;
          }
          else if(key<current.data){
              parent=current;
              current=current.lst;
          }
          else if(key>current.data){
              parent=current;
              current=current.rst;
          }
      }
      System.out.println("deleting:"+current.data);
      //--------1st case-----------
      if(current.lst==null && current.rst ==null){
          if(parent.lst==null){
              parent.rst=null;
          }
          else if(parent.rst==null){
              
                  parent.lst=null;
              }
          }
        //-----------2nd case ------------
      
      if(current.rst==null){
          parent.rst=current.lst;
      }
      else if(current.lst==null){
          parent.rst=current.lst;
      }
      
    return current;
      
      
    
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
    System.out.println("enter key :\n");
    int key=sc.nextInt();
    
    tree.search(root,key);
    //System.out.println(dkey.data);
    tree.delete(root,key);
    tree.inorder(root);
    
    
}    
}
