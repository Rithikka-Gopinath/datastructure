#include <stdio.h>
#include <stdlib.h>


typedef struct Node {
    int data;            
    struct Node *left;   
    struct Node *right;  
} Node;


Node* createNode(int data) {

    Node* newNode = (Node*)malloc(sizeof(Node));
    
  
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    
    return newNode;
}


void printNode(Node* node) {
    if (node != NULL) {
        printf("Node data: %d\n", node->data);
    }
}

int main() {
  
    Node* root = createNode(10);
    
    
    root->left = createNode(5);
    root->right = createNode(15);
    
    
    printNode(root);
    printNode(root->left);
    printNode(root->right);
    

    free(root->left);
    free(root->right);
    free(root);
    
    return 0;
}
