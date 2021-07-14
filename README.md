# fifth_task
// Inversion Count

#include <bits/stdc++.h>
using namespace std;
 
int countinv(int arr[], int n)
{
    int c = 0;
    for (int i = 0; i < n - 1; i++)
        for (int j = i + 1; j < n; j++)
            if (arr[i] > arr[j])
                c++;
 
    return c;
}

int main()
{
    int n;
    cin>>n;
    int arr[n];
    for(int i=0; i<n; i++){
        cin>>arr[i];
    }
 cout<<countinv(arr, n);
    return 0;
}

// Intersection of two linked list
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
       set<ListNode *>s;
        
        while(headB!=NULL){
            s.insert(headB);
            headB=headB->next;
        }
        while(headA!=NULL){
            if(s.find(headA)!=s.end())
                return headA;
            
            headA=headA->next;
        }
          
        return NULL;
    }
};

// length of linklist

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
 
class Solution {
public:
    int length(ListNode *head) {
       int c=0;
       while(head!=NULL){
        c++;
        head=head->next;
       }
       return c;
    }
};

// sort linklist

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* sortList(ListNode* head) {ListNode *h=head;
        vector<int>v;
        while(h!=NULL){
            v.push_back(h->val);
            h=h->next;
        }
        sort(v.begin(),v.end());
        ListNode *res=new ListNode(0);
        ListNode *t=res;
        for(int i=0;i<v.size();i++){
            t->next=new ListNode(v[i]);
            t=t->next;
        }
        return res->next;
        
    }
};

// palindrome linklist

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */

class Solution {
public:
    bool isPalindrome(ListNode* head) {
        vector<int> v;
        ListNode* cur=head;
        while(cur!=NULL){
            v.push_back(cur->val);
            cur=cur->next;
        }
        int n=v.size();
        for(int i=0;i<n/2;i++){
            if(v[i]!=v[n-i-1])return false;
        }
        return true;
    }
};


// reverse a linklist

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        if(head==NULL)
            return NULL;
        
        
        ListNode *p=head;
        ListNode *q=new ListNode(0);
        ListNode *d=q;
        int i;
        vector<int>r;
        while(p!=NULL){
            r.push_back(p->val);
            p=p->next;
        }
        int n=r.size();
        for(i=n-1;i>=0;i--){
            d->next=new ListNode(r[i]);
            d=d->next;
        }
        return q->next;
    }
};

// Deleting a node in linklist whose pointer to that node is given

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;
        node->next = node->next->next;
        
    }
};


// given a linked list arrange it in the below fashion
L0->Ln-1->L1->Ln-2->L2->Ln-3->null;

#include <iostream>
#include<vector>
using namespace std;

class ListNode
{
public:
    int val = 0;
    ListNode *next = nullptr;

    ListNode(int val)
    {
        this->val = val;
    }
};

void fold(ListNode *head)
{
    vector<ListNode*>v;
    ListNode *h=head;
    while(h!=NULL){
        v.push_back(h);
        h=h->next;
    }
    int i=0,j=v.size()-1;
    while(i<=j){
        if(h!=NULL)
        h->next=v[i];
        v[i]->next=v[j];
        h=v[j];
        i++;
        j--;
    }
    if(h) h->next=NULL;
    
}

void printList(ListNode *node)
{
    ListNode *curr = node;
    while (curr != nullptr)
    {
        cout << curr->val << " ";
        curr = curr->next;
    }
    cout << endl;
}

int main()
{
    int n;
    cin >> n;
    ListNode *dummy = new ListNode(-1);
    ListNode *prev = dummy;
    while (n-- > 0)
    {
        int val;
        cin >> val;
        prev->next = new ListNode(val);
        prev = prev->next;
    }

    ListNode *head = dummy->next;
    fold(head);
    printList(head);

    return 0;
}

// merge two sorted linklist

/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        ListNode * res;
        
        if(l1==NULL){
            return l2;
        }
        if(l2==NULL){
            return l1;
        }
        
        if(l1->val<=l2->val){
            res=l1;
            res->next=mergeTwoLists(l1->next,l2);
        }
        else{
            res=l2;
            res->next=mergeTwoLists(l1,l2->next);
        }
        
        return res;
    }
};

// implement of quick sort
#include<iostream>
#include<cstdlib>

using namespace std;

void swap(int *a, int *b) {
   int temp;
   temp = *a;
   *a = *b;
   *b = temp;
}

int Partition(int a[], int l, int h) {
   int pivot, index, i;
   index = l;
   pivot = h;
   for(i = l; i < h; i++) {
      if(a[i] < a[pivot]) {
         swap(&a[i], &a[index]);
         index++;
      }
   }
   swap(&a[pivot], &a[index]);
   return index;
}
int RandomPivotPartition(int a[], int l, int h) {
   int pvt, n, temp;
   n = rand();
   pvt = l + n%(h-l+1);
   swap(&a[h], &a[pvt]);
   return Partition(a, l, h);
}
int QuickSort(int a[], int l, int h) {
   int pindex;
   if(l < h) {
      pindex = RandomPivotPartition(a, l, h);
      QuickSort(a, l, pindex-1);
      QuickSort(a, pindex+1, h);
   }
   return 0;
}
int main() {
   int n, i;
   cout<<"\nEnter the number of data element to be sorted: ";
   cin>>n;
   int arr[n];
   for(i = 0; i < n; i++) {
      cout<<"Enter element "<<i+1<<": ";
      cin>>arr[i];
   }
   QuickSort(arr, 0, n-1);
   cout<<"\nSorted Data ";
   for (i = 0; i < n; i++)
      cout<<"->"<<arr[i];
   return 0;
}

// merge 2 linklist alternatively

void merge(Node *p, Node **q)
{
    Node *p_curr = p, *q_curr = *q;
    Node *p_next, *q_next;

    while (p_curr != NULL && q_curr != NULL)
    {
   
        p_next = p_curr->next;
        q_next = q_curr->next;
 
        q_curr->next = p_next; 
        p_curr->next = q_curr; 
 
      
        p_curr = p_next;
        q_curr = q_next;
    }
 
    *q = q_curr;
}


// implementation of merge Sort

#include<bits/stdc++.h>
using namespace std;

void merge(int arr[], int l, int mid, int r)
{
    int n1= mid-l+1;
    int n2 = r-mid;

    int a[n1];
    int b[n2];

    for(int i=0; i<n1; i++){
        a[i] = arr[i+l];
    }

    for(int i=0; i<n2; i++){
        b[i] = arr[mid+1+i];
    }
    int i=0;
    int j=0;
    int k=l;

    while(i<n1 && j<n2){
        if(a[i]<b[j]){
            arr[k]=a[i];
            k++;
            i++;
        }
        else{
            arr[k]=b[j];
            k++;
            j++;
        }
    }
    while(i<n1){
        arr[k]=a[i];
        k++;
        i++;
    }
    while(j<n2){
        arr[k]=b[j];
        k++;
        j++;
    }

}

void mergeSort(int arr[],int l,int r){
    if(l<r){
        int mid=(l+r)/2;
        mergeSort(arr,l,mid);
        mergeSort(arr,mid+1,r);
        merge(arr,l,mid,r);
    }
}
int main(){
    int n;
    cin>>n;
    int arr[n];


    for(auto &a:arr){
        cin>>a;
    }

    mergeSort(arr,0,n-1);

    for(auto v:arr){
        cout<<v<<" ";
    }
    
    return 0;

}
// reverse list in group of k
node* reverseK(node * head, int k){
    node *prevPtr=NULL;
    node *currPtr=head;
    node *nextPtr;

    int count=0;
    while(currPtr!=NULL && count<k){
        nextPtr=currPtr->next;
        currPtr->next=prevPtr;
        prevPtr=currPtr;
        currPtr=nextPtr;
        count++;
    }
    if(nextPtr!=NULL){
    head->next=reverseK(nextPtr, k);
    }

    return prevPtr;
}
