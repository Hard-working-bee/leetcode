class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int size = nums.size();
        int left = 0, right = 1;
        while(right < size){
            while(nums[left] == nums[right] && right - left < 2)
                right++;//维护2个指针，right 用来指向某一数字多出2的部分
            while(nums[left] == nums[right] && right < size){
                vector<int>::iterator iter = nums.begin() + right;
                nums.erase(iter);//用erase来删除这个指针（引用）
                size--;//更新大小
            }
            left = right;//更新左指针
            right++;
        }
        return size;
    }
};
 
