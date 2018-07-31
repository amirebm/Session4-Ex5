// برنامه ایی بنوسید که آرایی ایی از ورودی گرفته و عدد دیگری را بررسی کند که در آرایه وجود دارد یا نه 

# Session4-Ex5
package com.personal.Ex5;

import java.util.Scanner;

public class Ex5 {

	public static void main(String[] args) {
		
		Scanner sc= new Scanner(System.in);
		System.out.println("Enter a the size of array");
		int arrayLength=sc.nextInt();
		int num,index;
		int[] ar= new int[arrayLength];
		
		System.out.println("Please enter "+ arrayLength+ " numbers for array:");
		
		int i,j,t;
		ar[0]=sc.nextInt();
		for (i = 1; i < ar.length; i++) {
			
			ar[i]=sc.nextInt();
			t=ar[i];
			for ( j = i; j > 0; j--) {
				
				if(t>=ar[j-1])
					break;
				ar[j]=ar[j-1];
					
				
			}
			
			ar[j]=t;
		}	
		
		printArray(ar);
		
		System.out.println("Enter a number for searching");
		
		num=sc.nextInt();
		index=BinarySearch(ar, 0, ar.length, num);
		if (index==-1)
			System.out.println("the number is not found");
		else
			System.out.println("the number is found in " +(index+1)+ " of the array");

		System.out.println("Enter a number for searching by Sequential Searching");
		
		num=sc.nextInt();
		
		index=SequentialSearch(ar, num);

		if (index==-1)
			System.out.println("the number is not found");
		else
			System.out.println("the number is found in " +(index+1)+ " of the array");

		  }

	public static int SequentialSearch(int ar[], int num) {
		int i=0; 
		while (ar[i]!=num && i<ar.length) {
			i++;
			}
			 if(i==ar.length) 				 
				 return -1;
			 else
				 return i;
			 
			
			} 
	
	public static int BinarySearch(int[]ar,int low, int high,int num) {
		
		int middle = -1;
		if(low>high)
			return -1;
		else
		{
		 middle=(low +high)/2;
		if(num==ar[middle])
			return middle;
		else if(num<ar[middle])
			
		return BinarySearch(ar, low,middle-1,num);
		else
	    return BinarySearch(ar, middle+1,high-1,num);

		}
			}
   static void printArray(int arr[])
{
    int n = arr.length;
    for (int i=0; i<n; ++i)
        System.out.print(arr[i] + " ");
    System.out.println();
}
}
