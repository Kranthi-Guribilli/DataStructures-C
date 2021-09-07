# Implementation of an Array:
# Menu driven program for array operations in C
## Code snippet:
```c
#include<stdio.h>
#define MAXSIZE 40
int size;
//Traverse, insert, search and delete operations of the array are implemented by assuming that the array is unsorted array
void traverse(int arr[],int n);
void insert(int arr[],int n,int pos,int item);
int search(int arr[],int n,int item);//linear search is used in this program
void delete(int arr[],int n,int pos,int item);
void main(){
	int arr[MAXSIZE],pos,item,choice,del_item;
	char ch='y';
	printf("Enter the size of the array:");
	scanf("%d",&size);
	printf("Enter elements into the array:\n");
	//Initializing array by taking input from the user
	for(int i=0;i<size;i++){
		printf("Element-%d:",i);
		scanf("%d",&arr[i]);
	}
	system("cls");
	do{
	printf("\n \t\t MENU:");
	printf("\n 1. Traverse\n 2. Insert\n 3. Delete\n 4. Search");
	printf("\nEnter your choice:");
	scanf("%d",&choice);
	switch(choice){
		case 1:
			traverse(arr,size);
			break;
		case 2:
			printf("Enter position:");
			scanf("%d",&pos);
			printf("Enter element to insert:");
			scanf("%d",&item);
			insert(arr,size++,pos,item);
			break;
		case 3:
			printf("Enter element to be deleted:");
			scanf("%d",&del_item);
			pos=search(arr,size,del_item);
			if(pos==-1){
				printf("\nElement not found");
				break;
			}
			delete(arr,size--,pos,del_item);
			break;
		case 4:
			printf("Enter the element to be searched:");
			scanf("%d",&item);
			pos=search(arr,size,item);
			(pos==-1)?printf("Element is not present in array"):printf("Element is present at index %d",pos);
			break;
		default:
			printf("\nEntered wrong choice!!");
	}
		printf("\nDo you want to continue?(y/n): ");
		scanf("%s",&ch);
		system("cls");
		}while(ch=='y');
}
//An utility function to traverse the array
void traverse(int arr[],int size){
	printf("Array: ");
	for(int i=0;i<size;i++){
		printf("%d ",arr[i]);
	}
	printf("\n");
}

//An utility function to insert an element at a position
void insert(int arr[],int n,int pos,int item){
	n++;
    // shift elements forward
    for (int i=n-1; i >= pos; i--)
        arr[i] = arr[i-1];
 
    // insert x at pos
    arr[pos] = item;
}
//Function to search for an element
int search(int arr[],int n,int x){
	for(int i=0;i<n;i++){
		if(arr[i]==x)
			return i;
	}
	return -1;
}
//Function to delete an element from the array
void delete(int arr[],int n,int pos,int item){
	for(int i=pos;i<n;i++){
		arr[i]=arr[i+1];
	}
	n--;
}
```