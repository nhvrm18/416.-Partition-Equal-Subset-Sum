# 416.-Partition-Equal-Subset-Sum
leetcode

class Solution {
public:
    bool subsetsum(vector<int> nums,int sum,int n)
    {
        bool t[n+1][sum+1];
        for(int i=0;i<n+1;i++)
        {
            for(int j =0;j<sum+1;j++)
            {
                if(i==0)
                    t[i][j] = false;
              else  if(j==0)
                    t[i][j] = true;
                else
                {
                    if(nums[i-1] <= j)
                    t[i][j] = t[i][j-nums[i-1]] || t[i-1][j];
                    else
                    t[i][j] = t[i-1][j];
                }
                 
                
            }
        }
        return t[n][sum];
    }
    bool canPartition(vector<int>& nums) {
        int n = nums.size();
        int sum =0;
        bool ans = false;
        for(int i=0;i<n;i++)
        {
            sum = sum + nums[i];
            
        }
        if(sum % 2 != 0 || n %2 != 0)
            return false;
        if(sum % 2 == 0)
        {
           ans = subsetsum(nums,sum/2,n);
        }
        return ans;
    }
};
