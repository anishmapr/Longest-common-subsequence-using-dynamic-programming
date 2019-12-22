# Longest-common-subsequence-using-dynamic-programming

# QUESTION:

Given two Strings S1 and S2 write a program to find the longest common subsequence using Dynamic programming
LCS - longest common subsequence

Input:

AGGTAB

GXTXAYB

Output:

LCS length is 4


# CODE

    #include<stdio.h>
    #include<string.h>
    #include<stdlib.h>
    int max(int num1,int num2)
    {
        return num1>num2?num1:num2;
    }

    int LCS(char *str1,char *str2,int len1,int len2)
    {
         int L[len1+1][len2+1]; 
    
    for(int ind1=0;ind1<=len1;ind1++){
        for(int ind2=0;ind2<=len2;ind2++){
           if(ind1==0 || ind2==0){
               L[ind1][ind2]=0;
           }
           else if(str1[ind1-1] == str2[ind2-1]){
               L[ind1][ind2]=L[ind1-1][ind2-1] + 1;
           }
           else{
               L[ind1][ind2]=max(L[ind1-1][ind2],L[ind1][ind2-1]);
           }
        }
    }
    return L[len1][len2];
    }
    int main()
    {
         char str1[1000],str2[1000];   
         scanf("%s",str1);                    //input first string
         scanf("%s",str2);                    //input second string
         int len1=strlen(str1);               //length of first string
         int len2=strlen(str2);               //length of second string
         
         printf("LCS length is %d",LCS(str1,str2,len1,len2));    //calling the function to find LCS
    }

