# 3Sum
Actually this is a search problem I think. As we all know the two sum problem can be easily solved with two pointers so in the 3 Sum problem we can use one number as a target and then do the two sum problem
```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res=new ArrayList<List<Integer>>();
        if(nums.length==0)return res;
        Arrays.sort(nums);
        for(int i=0;i<nums.length-2;i++)
        {
            if(i>0&&nums[i]==nums[i-1])continue;
            int target=0-nums[i];
            int begin=i+1;
            int end=nums.length-1;
            while(begin<end) // for each target we should extract all two sum results
            {
                List<Integer> cur=new ArrayList<Integer>();
                cur.add(nums[i]);
                if(nums[begin]+nums[end]!=target)
                {
                    if(nums[begin]+nums[end]<target)
                        begin++;
                    else
                      end--;
                }
                if(begin<end&&nums[begin]+nums[end]==target)
                {
                    cur.add(nums[begin]);
                    cur.add(nums[end]);
                    res.add(cur);
                    while(begin<end&&nums[begin]==cur.get(1))begin++; // this code is used to advoid duplicate result
                    while(begin<end&&nums[end]==cur.get(2))end--;// this code is used to advoid duplicate result
                }
            }
        }
            
        return res;
    }
    
}
```
