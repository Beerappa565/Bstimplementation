
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
struct node
{
  int data;
  struct node *left;
  struct node *right;
};

struct node *
createNode (int value)
{
  struct node *newNode = malloc (sizeof (struct node));
  newNode->data = value;
  newNode->left = NULL;
  newNode->right = NULL;

  return newNode;
}
struct node *
insert (struct node *root, int data)
{
  if (root == NULL)
    return createNode (data);

  if (data < root->data)
    root->left = insert (root->left, data);
  else if (data > root->data)
    root->right = insert (root->right, data);

  return root;
}
void inorder (struct node *root)
{
  
  if (root == NULL)
    return;

 inorder (root->left);
  printf (":%d -> ", root->data);
  inorder(root->right);
}
void preorder (struct node *root)
{
    
  if (root == NULL)
    return;
   printf (" :%d ->", root->data);
  preorder(root->left);
  preorder(root->right);
 
}
void postorder (struct node *root)
{

  if (root == NULL)
    return;

  postorder(root->left);
  postorder(root->right);
    printf (":%d ->", root->data);
}
int findmin(struct node* root)
{
    if(root==NULL)
    { 
       
        return -1;
      
    }
    else if(root->left==NULL)
    {
        return root->data;
    }
   
       return findmin(root->left);
    
}
int findmax(struct node* root)
{
    if(root==NULL)
    { 
       
        return -1;
      
    }
    else if(root->right==NULL)
    {
        return root->data;
    }
   
       return findmax(root->right);
    
}
int findheight(struct node* root)
{
    int x,y;
    if(root==NULL)
    {
        return-1;
    }
    x=findheight(root->left);
     y=findheight(root->right);
    if(x>y)
    return x+1;
    else
    return y+1;
}


int
main ()
{
  struct node *root = NULL;
  root = insert (root, 8);
  root=insert(root,7);
  root=insert(root,6);
  root = insert (root, 3);
  root = insert (root, 1);
  root = insert (root, 6);
  
  root = insert (root, 10);
  root = insert (root, 14);
  root = insert (root, 4);
   root = insert (root, 56);
    root = insert (root, 334);
     root = insert (root, 48);
    printf("inorder traversal");
     inorder(root);
       printf("\npreorder traversal");
    preorder(root);
      printf("\npostorder traversal");
    postorder(root);
   printf("\nminelement:%d",findmin(root));
   printf("\nmaxelement:%d",findmax(root));
   printf("\nheight:%d",findheight(root));

}
