# frog-jump
//recursion solution 
#include <bits/stdc++.h> 

int f(vector<int>heights, int n ){

        if(n==0) return 0; 

    int left = f(heights, n-1)+ abs(heights[n]-heights[n-1]);

    int right = INT_MAX; 

    if(n>1) right = f(heights,n-2) + abs(heights[n]-heights[n-2]); 

    return min(left, right);  
}
int frogJump(int n, vector<int> &heights)
{

   return f(heights,n-1); 

}

        
        
        
        
tabulation   dp 

#include <bits/stdc++.h> 

int f(vector<int>heights, int n,vector<int>&dp){

        if(n==0) return 0; 
if (dp[n]!=-1)  return dp[n]; 
    int left = f(heights, n-1,dp)+ abs(heights[n]-heights[n-1]);

    int right = INT_MAX; 

    if(n>1) right = f(heights,n-2,dp) + abs(heights[n]-heights[n-2]); 

    return dp[n] = min(left, right);  
}
int frogJump(int n, vector<int> &heights)
{
    vector<int>dp(n+1,-1); 
   return f(heights,n-1,dp); 

}
        
        
        

//space complexity reduce to o(1)

#include <bits/stdc++.h> 
int frogJump(int n, vector<int> &heights)
{
   int prev =0 ; 
   int prev2 =0; 
    
    for(int i=1; i<n; i++){
            
       int left =  prev + abs(heights[i] - heights[i-1]);
       
       int right = INT_MAX; 
       
       if(i>1) {

            right = prev2 + abs(heights[i])-abs(heights[i-2]);  
       }  

       int curr = min(left, right); 
       prev2 =prev; 
       prev =curr; 
       
    }  

    return prev;  
}
