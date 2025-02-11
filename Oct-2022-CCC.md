# Oct 2022 : CCC SRMIST KTR : CPS 02 : Sprint II Coding

### P 501 - Orange Partitioning 
![c](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
```c
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

int main() {
    int n;
    scanf("%d",&n);
    int a[n];
    for(int i=0;i<n;i++)
        scanf("%d",&a[i]);
    int k=0;
    for(int i=0; i<n-1; i++)
        {
            if (a[i]<= a[n-1])
            {
                int t = a[i];
                a[i]= a[k];
                a[k++] = t;
            }
        }
        int t = a[n-1];
        a[n-1]= a[k];
        a[k] = t;
    for(int i=0;i<n;i++)
        printf("%d ",a[i]);
  
    return 0;
}
```

### P 502 - Tisha and Orange Sorting
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def swap(a,b):
    temp = a
    a = b
    b = temp
    return a,b
def partition(a,l,r):
    x = a[r]
    i = l-1
    for j in range(l,r):
        if(a[j]<=x):
            i = i+1
            a[i],a[j] = swap(a[i],a[j])
    a[i+1],a[r] = swap(a[i+1],a[r])
    return (i+1)xq
def Quicksort(a,l,r):
    if l<r:
        p = partition(a,l,r)
        print(p)
        for i in range(l,r+1):
            print(a[i],end=" ")
        print()
        Quicksort(a,l,p-1)
        Quicksort(a,p+1,r)
n = int(input())
a = list(map(int,input().split()))
Quicksort(a,0,n-1)
```

### P 503 - One Teacher Two Classes
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def mergeArrays(arr1, arr2, n1, n2, arr3):
    i = 0
    j = 0
    k = 0
    while i<n1 and j <n2:
        if arr1[i] < arr2[j]:
            arr3[k] = arr1[i]
            k += 1
            i += 1
        else:
            arr3[k] = arr2[j]
            k += 1
            j += 1
    while i < n1:
        arr3[k] = arr1[i]
        k += 1
        i += 1
    while j < n2:
        arr3[k] = arr2[j]
        k += 1
        j += 1

n = int(input())
a = list(map(int, input().split()))
m = int(input())
b = list(map(int, input().split()))
c = [0]*(n+m)
mergeArrays(a, b, n, m, c)
for i in range(n+m):
    print(c[i], end=" ")
```

### P 504 - Vasya and Birthday Presents
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def merge(start,mid,end,a):
    arr = [0] * (end-start+1)
    p=start
    q=mid+1
    k=0
    i=0
    
    for i in range(start,end+1):
        if p > mid:
            arr[k]=a[q]
            q+=1
        elif ( q > end):
            arr[k]=a[p]
            p+=1
        elif(a[p]>a[q]):
            arr[k]=a[p]
            p+=1
        else:
            arr[k]=a[q]
            q+=1
        k+=1
    
    for i in range(start,end+1):
        a[i]=arr[i-start]

def mergesort(start,end,a):
    if start<end:
        mid=(start+end)//2
        mergesort(start,mid,a)
        mergesort(mid+1,end,a)
        
        merge(start,mid,end,a)
    
t = int(input())
l = 0

while l<t:
    n = int(input())
    a = list(map(int,input().split()))
    start=0
    end=n-1
    mergesort(start,end,a)
    for i in range(n):
        print(a[i],end=" ")
    print()
    l+=1
```

### Q 101 - Trees - Inorder Traversal
![c](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <math.h>
#define scan(x) scanf(" %d", &x)
struct TreeNode {
	int x;
	struct TreeNode* L;
	struct TreeNode* R;
};
typedef struct TreeNode TreeNode;
TreeNode* newNode(int _x) {
	TreeNode* node = (TreeNode*) malloc(sizeof(TreeNode));
	node->x = _x;
	node->L = node->R = NULL;
  return node;
}
TreeNode* insert(TreeNode* node, int val) {
	if (node == NULL) return newNode(val);
	if (val <= node->x) node->L = insert(node->L, val);
	else node->R = insert(node->R, val);
return node;
}

/*********************************************************/

void inorder(TreeNode* Root)
{

   if (Root == NULL) return;
    inorder(Root->L);
    printf("%d ", Root->x);
    inorder(Root->R);

}

/*******************************************************/

int main() {
	int val, N; scan(N);
	TreeNode* Root = NULL;
	for (int i = 1; i <= N; i++) {
		scan(val);
		Root = insert(Root, val);
	}
	inorder(Root);
}
```

### Q 102 - Trees - Preorder Traversal
![c](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <math.h>
#define scan(x) scanf(" %d", &x)
struct TreeNode {
	int x;
	struct TreeNode* L;
	struct TreeNode* R;
};
typedef struct TreeNode TreeNode;
TreeNode* newNode(int _x) {
	TreeNode* node = (TreeNode*) malloc(sizeof(TreeNode));
	node->x = _x;
	node->L = node->R = NULL;
    return node;
}
TreeNode* insert(TreeNode* node, int val) {
	if (node == NULL) return newNode(val);
	if (val <= node->x) node->L = insert(node->L, val);
	else node->R = insert(node->R, val);
    return node;
}

/*******************************************************************/

void preorder(struct TreeNode* Root) {
    if (Root == NULL) return;
    printf("%d ", Root->x);
    preorder(Root->L);
    preorder(Root->R);
} 

/*******************************************************************/

int main() {
	int val, N; scan(N);
	TreeNode* Root = NULL;
	for (int i = 1; i <= N; i++) {
		scan(val);
		Root = insert(Root, val);
	}
	preorder(Root);
}
```

### Q 103 - Trees - Postorder Traversal
![c](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <math.h>
#define scan(x) scanf(" %d", &x)
struct TreeNode {
	int x;
	struct TreeNode* L;
	struct TreeNode* R;
};
typedef struct TreeNode TreeNode;
TreeNode* newNode(int _x) {
	TreeNode* node = (TreeNode*) malloc(sizeof(TreeNode));
	node->x = _x;
	node->L = node->R = NULL;
    return node;
}
TreeNode* insert(TreeNode* node, int val) {
	if (node == NULL) return newNode(val);
	if (val <= node->x) node->L = insert(node->L, val);
	else node->R = insert(node->R, val);
    return node;
}

/*******************************************************************/
// Your code here

void postorder(struct TreeNode* Root) {
    if (Root == NULL) return;
    postorder(Root->L);
    postorder(Root->R);
    printf("%d ", Root->x);
}  

/*******************************************************************/

int main() {
	int val, N; scan(N);
	TreeNode* Root = NULL;
	for (int i = 1; i <= N; i++) {
		scan(val);
		Root = insert(Root, val);
	}
	postorder(Root);
}
```

### Q 301 - Trees - Height of a Binary Tree
![c](https://img.shields.io/badge/C-00599C?style=for-the-badge&logo=c&logoColor=white)
```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

struct node {
    int data;
    struct node *left;
    struct node *right;
};

struct node *createNode(int data) {
    struct node *newNode = (struct node *) malloc(sizeof(struct node));
    newNode->data = data;
    newNode->left = NULL;
    newNode->right = NULL;
    return newNode;
}

struct node *insert(struct node *root, int data) {
    if (root == NULL) {
        return createNode(data);
    } else {
        struct node *cur;
        if (data <= root->data) {
            cur = insert(root->left, data);
            root->left = cur;
        } else {
            cur = insert(root->right, data);
            root->right = cur;
        }
        return root;
    }
}

int height(struct node *root) {
    // Write your code here.
    if (root == NULL) {
        return -1;
    }
    return 1 + fmax(height(root->left), height(root->right));
}

int main(void) {
    int t;
    scanf("%d", &t);
    struct node *root = NULL;
    while (t-- > 0) {
        int data;
        scanf("%d", &data);
        root = insert(root, data);
    }
    int heightOfTree = height(root);
    printf("%d", heightOfTree);
    return 0;
}
```

### Z 460 Date Sorting
![CPP](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
``` cpp
#include <iostream>
#include <string>
#include <cmath>
#include <cstdlib>
using namespace std;
struct Date{
    int d,m,y;
};
int main() {
    int t,i,j;
    cin>>t;
    struct Date date[t];
    for(i=0;i<t;i++){
        cin>>date[i].d>>date[i].m>>date[i].y;
    }
    for(i=0;i<t-1;i++){
        for(j=i+1;j<t;j++){
            if(date[i].y > date[j].y){
                struct Date temp = date[i];
                date[i] = date[j];
                date[j] = temp;
            }
            if(date[i].y == date[j].y){
                if(date[i].m>date[j].m){
                    struct Date temp = date[i];
                    date[i] = date[j];
                    date[j] = temp;
                }
            }
            if(date[i].y == date[j].y && date[i].m == date[j].m){
                if(date[i].d>date[j].d){
                    struct Date temp = date[i];
                    date[i] = date[j];
                    date[j] = temp;
                }
            }
        }
    }
    for(i=0;i<t;i++){
        cout<<date[i].d<<" "<<date[i].m<<" "<<date[i].y<<endl;
    }
    return 0;
}
```

### Q 501 - Mirror Tree
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def main():
    N = int(input())
    nodes = {}
    for i in range(N - 1):
        parent, child, direction = input().split()
        parent = int(parent)
        child = int(child)
        if direction == "R":
            populateMapForRightNode(parent, child, nodes)
        else:
            populateMapForLeftNode(parent, child, nodes)
    root = nodes[1]
    nodes = {}
    for i in range(N - 1):
        parent, child, direction = input().split()
        parent = int(parent)
        child = int(child)
        if direction == "R":
            populateMapForRightNode(parent, child, nodes)
        else:
            populateMapForLeftNode(parent, child, nodes)
    root1 = nodes[1]
    is_mirror_binary_trees = is_mirror_tree(root, root1)
    if is_mirror_binary_trees:
        print("yes")
    else:
        print("no")
def is_mirror_tree(tree, mirror_tree):
    if tree is None and mirror_tree is None:
        return True
    if tree is None or mirror_tree is None:
        return False
    if tree.item != mirror_tree.item:
        return False
    if not is_mirror_tree(tree.left, mirror_tree.right):
        return False
    if not is_mirror_tree(tree.right, mirror_tree.left):
        return False
    return True
def populateMapForRightNode(parent, child, nodes):
    if nodes.get(parent) is None:
        node = Node(parent)
        node.right = Node(child)
        nodes[parent] = node
        nodes[child] = node.right
    else:
        node = nodes.get(parent)
        node.right = Node(child)
        nodes[child] = node.right
def populateMapForLeftNode(parent, child, nodes):
    if nodes.get(parent) is None:
        node = Node(parent)
        node.left = Node(child)
        nodes[parent] = node
        nodes[child] = node.left
    else:
        node = nodes.get(parent)
        node.left = Node(child)
        nodes[child] = node.left
class Node:
    def __init__(self, item):
        self.item = item
        self.left = None
        self.right = None
main()
```

### Q 502 - Inorder Traversal of a Binary Tree
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
class newNode:
    def __init__(self, data):
        self.data = data
        self.left = self.right = None

def insertLevelOrder(arr, i, n):
    root = None
    # Base case for recursion
    if i < n:
        root = newNode(arr[i])

        # insert left child
        root.left = insertLevelOrder(arr, 2 * i + 1, n)

        # insert right child
        root.right = insertLevelOrder(arr, 2 * i + 2, n)

    return root


def inOrder(root):
    if root != None and root.data != 0:
        inOrder(root.left)
        print(root.data, end=" ")

        inOrder(root.right)


# Driver Code
if __name__ == '__main__':
    n = int(input())
    arr = list(map(int, input().split()))
    root = None
    root = insertLevelOrder(arr, 0, n)
    inOrder(root)

```

### Q 801 - Zig Zag Traversal
![CPP](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
``` cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
int a[100000][2];
int stack1[100000],stack2[10000];
int main() {
     int parent,child;
    char ch;
    int n;
    cin>>n;
    for(int i=0;i<100000;i++)
        for(int j=0;j<2;j++)
            a[i][j]=-1;
    for(int i=1;i<n;i++)
    {
        cin>>parent>>child>>ch;
        if(ch=='L')
        {
            a[parent][0]=child;
        }
        else
            a[parent][1]=child;
    }
    int head1=-1,head2=-1;
        stack1[++head1]=1;
    while(head1!=-1)
    {
        while(head1!=-1)
        {
            if(a[stack1[head1]][0]!=-1)
                stack2[++head2]=a[stack1[head1]][0];
            if(a[stack1[head1]][1]!=-1)
                stack2[++head2]=a[stack1[head1]][1];
            cout<<stack1[head1--]<<" ";
        }
        while(head2!=-1)
        {
             if(a[stack2[head2]][1]!=-1)
                stack1[++head1]=a[stack2[head2]][1];
            if(a[stack2[head2]][0]!=-1)
                stack1[++head1]=a[stack2[head2]][0];
            cout<<stack2[head2--]<<" ";
        }
    }
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */   
    return 0;
}
```

### Q 802 - Inorder Traversal Restoration
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def convert(post):
    if len(post) == 1:
        return post
    left = post[:len(post)//2]
    right = post[len(post)//2:len(post)-1]
    root = post[len(post)-1]
    return convert(left) + root + convert(right)

post = input()

print(convert(post))


```
### CCT A4 - Greatest Number with the Digits
![Python](https://img.shields.io/badge/Python3-FFD43B?style=for-the-badge&logo=python&logoColor=blue)
```python
def printMaximum(inum):
 
    count = [0 for x in range(10)]
 
    string = str(num)
 
    for i in range(len(string)):
        count[int(string[i])] = count[int(string[i])] +  1
 
    result = 0
    multiplier = 1
 
    for i in range(10):
        while count[i] > 0:
            result = result + ( i * multiplier )
            count[i] = count[i] - 1
            multiplier = multiplier * 10
 
    return result
 

num = input()
print(printMaximum(num))
```

### Contacts Application 
![cpp](https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
```cpp
#include <cmath>
#include <cstdio>
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;
#define ALPHABET_SIZE 26

int getChildIndex(char c)
{
    return (int)c - 'a';
}

struct node
{
    char data;
    int suffixes;
    node *child[ALPHABET_SIZE];
    
    node(char d)
    {
        data = d;
        suffixes = 0;
        for(int i=0; i<ALPHABET_SIZE; i++)
        {
            child[i] = NULL;    
        }
    }
};

void addWord(node *root, string word)
{
    node *temp = root;
    for(int i=0; i<word.length(); i++)
    {
        char c = word[i];
        int index = getChildIndex(c);
        if(temp->child[index] == NULL)
            temp->child[index] = new node(c);    
        temp = temp->child[index];
        temp->suffixes++;
    }
}

void countWords(node *root, string word)
{
    node *temp = root;
    for(int i=0; i<word.size(); i++)
    {
        char c = word[i];
        int index = getChildIndex(c);
        if(temp->child[index] == NULL)
        {
            cout << "0\n";
            return;
        }
        temp = temp->child[index];
    }
    
    cout << temp->suffixes << endl;
}

int main() {
    /* Enter your code here. Read input from STDIN. Print output to STDOUT */  
    int n;
    cin >> n;
    
    node *root = new node('0');
    
    for(int i=0; i<n; i++)
    {
        string op, word;
        cin >> op >> word;
        
        if(op == "add")
        {
            addWord(root, word);
        }
        else
        {
            countWords(root, word);    
        }
    }
    return 0;
}
```
