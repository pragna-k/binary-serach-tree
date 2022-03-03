# binary-serach-tree
#include<stdio.h>

#include<stdlib.h>

struct BST

{

        int data;

        struct BST *left,*right;

};

typedef struct BST node;

node *insert(node *p,int x)

{

        node *new;

        if(p==NULL)

        {

                new=(node*)malloc(sizeof(node));

                new->data=x;

                new->left=NULL;

                new->right=NULL;

                p=new;

        }

        else if(x<=p->data)

        {

                p->left=insert(p->left,x);

        }

        else if(x>p->data)

        {

                p->right=insert(p->right,x);

        }

        return p;

}

void inorder(node *p)

{

        if(p!=NULL)

        {

                inorder(p->left);

                printf("%d\t",p->data);

                inorder(p->right);

        }

}

void preorder(node *p)

{

        if(p!=NULL)

        {

                printf("%d\t",p->data);

                preorder(p->left);

                preorder(p->right);

        }

}

void postorder(node *p)

{

        if(p!=NULL)

        {

                postorder(p->left);

                postorder(p->right);

                printf("%d\t",p->data);

        }

}

node *findMin(node *p)

{

        if(p!=NULL)

        {

                while(p->left!=NULL)

                {

                        p=p->left;

                }

        }

        return p;

}

node *findMax(node *p)

{

        if(p!=NULL)

        {

                while(p->right!=NULL)

                {

                        p=p->right;

                }

        }

        return p;

}

node *search(node *p,int x)

{

        if(p==NULL)

        {

                return p;

        }

        else if(p->data>x)

        {

                return search(p->left,x);

        }

        else if(p->data<x)

        {

                return search(p->right,x);

        }

        else

        {

                return p;

        }

}

node *delete(node *p,int x)

{

        node *temp;

        if(p==NULL)

        {

                return p;

        }

        else if(p->data>x)

        {

                p->left=delete(p->left,x);

        }

        else if(p->data<x)

        {

                p->right=delete(p->right,x);

        }

        else if(p->left!=NULL&&p->right!=NULL)

        {

                x=p->data=findMin(p->right)->data;

                p->right=delete(p->right,x);

        }

        else

        {

                temp=p;

                if(p->right==NULL)

                {

                        p=p->left;

                }

                else if(p->left==NULL)

                {

                        p=p->right;

                }

                free(temp);

        }

        return p;

}

void main()

{

        node *root=NULL,*temp;

        int x,ch;

        printf("1.INSERT\n2.INORDER\n3.PREORDER\n4.POSTORDER\n5.FIND MINIMUM\n6.FIND MAXIMUM\n7.SEARCH\n8.DELETE\n9.EXIT\n");

        while(1)

        {

                printf("Enter your choice:\n");

                scanf("%d",&ch);

                switch(ch)

                {

                        case 1: printf("Enter the element into the binary search tree: ");

                                scanf("%d",&x);

                                root=insert(root,x);

                                break;

                        case 2: printf("The inorder traversal of the binary search tree is : ");

                                inorder(root);

                                break;

                       case 3: printf("The preorder traversal of the binary search tree is : ");

                                preorder(root);

                                break;

                        case 4: printf("The postorder traversal of the binary search tree is : ");

                                postorder(root);

                                break;

                        case 5: temp=findMin(root);

                                if(temp==NULL)

                                {

                                        printf("Nothing to display");

                                }

                                else

                                {

                                        printf("The minimum element is %d\n",temp->data);

                                }

                                break;

                        case 6:temp=findMax(root);

                               if(temp==NULL)

                               {

                                       printf("Nothing to display");

                               }

                               else

                               {

                                       printf("The maximum element is %d\n",temp->data);

                               }

                               break;

                        case 7:printf("Enter the element to search: ");

                               scanf("%d",&x);

                               temp=search(root,x);

                               if(temp==NULL)

                               {

                                       printf("The element %d not found",x);

                               }

                               else

                               {

                                       printf("%d is found",x);

                               }

                        case 8: printf("Enter the element to delete: ");

                                scanf("%d",&x);

                                root=delete(root,x);

                                break;

                        case 9:exit(0);

                               break;

                }

        }

}


output:
1.INSERT
2.INORDER
3.PREORDER
4.POSTORDER
5.FIND MINIMUM
6.FIND MAXIMUM
7.SEARCH
8.DELETE
9.EXIT
Enter your choice:
1
Enter the element into the binary search tree: 25
Enter your choice:
2
The inorder traversal of the binary search tree is : 25 Enter your choice:
3
The preorder traversal of the binary search tree is : 25        Enter your choice:
4
The postorder traversal of the binary search tree is : 25       Enter your choice:
5
The minimum element is 25
Enter your choice:
6
The maximum element is 25
Enter your choice:
7
Enter the element to search: 25
25 is foundEnter the element to delete: 8
Enter your choice:
8
Enter the element to delete: 25
Enter your choice:
1
Enter the element into the binary search tree: 25
Enter your choice:
9
