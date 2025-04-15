class Solution {
public:
 bool setpart(vector<int>&nums,int n ,int sum,vector<vector<int>>&dp){
    if(n==0){
        return false;
    }
    if(sum==0){
        return true;
    }
    if(dp[n][sum]!=-1){
        return dp[n][sum];
    }
    if(nums[n-1]>sum){
        return setpart(nums,n-1,sum,dp);
    }

         return dp[n][sum]= setpart(nums,n-1,sum,dp)||setpart(nums,n-1,sum-nums[n-1],dp);
    
 }
    bool canPartition(vector<int>& nums) {
        int n=nums.size();
        int sum=0;
        for(int i=0; i<n; i++){
            sum+=nums[i];

        }
        if(sum%2!=0){
            return false;
        }
        int target=sum/2;
        vector<vector<int>>dp(n+1,vector<int>(target+1,-1));
        return setpart(nums,n,target,dp);
        
    
        
    }
};
