# program-4
9. Yatin plays PUBG
Yatin is playing PUBG and he has reached a place with a large staircase in front of him.
And there is an enemy at each landing of the staircase.
The staircase is analogous to a binary tree with each of its nodes as a landing of the
staircase and each of its edges as stairs from one landing to another.

Yatin wants to kill the maximum possible number of enemies. He can kill every person
he can see from his position with his suppressed sniper gun. But he can see only the
persons at the leftmost standing at each level and cannot see the rest.
Before starting shooting them, he wants to know how many persons he can kill. He is
busy keeping an eye on the enemies. So he wants you to find out the maximum
number of people he can kill from that location by providing you with the analogous
a binary search tree.

#include<stdio.h>
#include<stdlib.h>
#include <iostream>
using namespace std;
struct node{
long data;
node *left;
node *right;
};
typedef node *tree;
tree root;
long count;
tree find (tree temp, long val){
if(temp==NULL){

return temp;}
else if(temp->data==val) return temp;
else if(temp->data<val&&temp->right!=NULL) return find(temp->right,val);
else if(temp->data>val&&temp->left!=NULL) return find(temp->left,val);
else { return temp;}
}
void insert(long val){
tree place,temp;
place=find(root,val);
if(place==NULL){
root=(tree)malloc(sizeof(node));
root->data=val;
root->left=NULL;
root->right=NULL;
count++;
}
else if(place->data>val){
place->left=(tree)malloc(sizeof(node));
place->left->data=val;
place->left->left=NULL;
place->left->right=NULL;
}
else if(place->data<val){
place->right=(tree)malloc(sizeof(node));
place->right->left=NULL;
place->right->right=NULL;
place->right->data=val;

}

}
void print(tree temp){
if(temp==NULL) return ;
else {

print(temp->left);
print(temp->right);
}
}
long maxDepth(tree node)
{
if (node==NULL){
return 0;
count++;
}
else
{

long lDepth = maxDepth(node->left);
long rDepth = maxDepth(node->right);

if (lDepth > rDepth)
return(lDepth+1);
else
return(rDepth+1);
}
}
int main()
{
long n,m,t,k;
cin>>t;
long i;
for(i=0; i < t; i++){
root=NULL;
cin>>n;
for(int j=0;j<n;j++){
cin>>k;
insert(k);
}
cout<< maxDepth(root)<<"\n";

}

return 0;
}
