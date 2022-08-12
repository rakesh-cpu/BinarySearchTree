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
     // char ch="l";
      boolean found=false;
      while(found!=true && current!=null){
          if(current.data==key){
              
              found=true;
          }
          else if(key<current.data){
              //ch="l";
              parent=current;
              current=current.lst;
          }
          else if(key>current.data){
              //ch="r";
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
          /*else if(parent.lst!=null && parent.rst!=null)
          {
               parent.lst=null;
               parent.rst=null;
          }*/
          
          
      
          
        //-----------2nd case ------------
      
      if(current.rst==null && current.lst!=null){
          if(parent.data>current.data){
              
          
             parent.lst=current.lst;
          }
          else if(parent.data<current.data){
              parent.rst=current.lst;
          }
      }
      else if(current.lst==null && current.rst!=null){
          if(parent.data>current.data){
              parent.lst=current.rst;
              
          }
          else if(parent.data<current.data){
          parent.rst=current.rst;
          }
          
      }
      //------------3rd case----------
      if(current.lst!=null && current.rst!=null){
          node suc=current.rst;
          node pre=null;
          while(suc.lst!=null){
              pre=suc;
              suc=suc.lst;
              
          }
          if(suc.rst!=null){
              pre.lst=suc.rst;
          }
          //suc.rst=pre.rst;
          suc.lst=current.lst;
          if(parent.data>current.data){
             parent.lst=suc;
          }
          else if(parent.data<current.data){
              parent.rst=suc;
          }
          
          
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
    System.out.println();
    tree.inorder(root);
    System.out.println();
    System.out.println("enter key :");
    int key=sc.nextInt();
    //System.out.println();
    
    //tree.search(root,key);
    //System.out.println(dkey.data);
    tree.delete(root,key);
    System.out.println();
    tree.inorder(root);
    
    
}    
}
