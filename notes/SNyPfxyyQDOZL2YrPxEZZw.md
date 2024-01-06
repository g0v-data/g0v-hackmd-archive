# LeetCode contest 334
這邊會記錄本周LEETCODE CONTEST的題目!
但是第四題太難了就先不記錄了

----
先記錄一下我這周的比賽成績
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_88ed1a2d79f1921be628adaeecc92db8.png)
可改進之處:
第一題光處理一堆鳥BUG就浪費40分鐘了
然後自己也要多加油早點起床先準備好才能一開始就進入狀況。

----
第一題: Left and Right Sum Differences
https://leetcode.com/problems/left-and-right-sum-differences/description/
實做複雜度:O(N)
使用技巧:就很基本的ARRAY/VECTOR題目
```class Solution {
public:
    vector<int> leftRigthDifference(vector<int>& nums) { 
        int n=nums.size()-1;
        vector<int>ii(n+1);
        vector<int>jj(n+1);
        vector<int>kk(n+1);
        ii.push_back(0);
        jj[0]=0;
        int tmp=0;
         for(int i=1;i<=n;i++)
        {
            ii[i]=ii[i-1]+nums[i-1];
        }
        int r=1;
         for(int i=n;i>0;i--)
        {
            jj[r]=jj[r-1]+nums[i];            
            r++;
        }
        for(int i=0;i<=n;i++)
        {
            kk[i]=abs(jj[n-i]-ii[i]);
            cout<< ii[i]<<' '<<jj[n-i]<<endl;    
        }
        return kk;      
    }
    };
```
可以看到我那時候考試寫得真的很粗糙，多用了一堆MEMORY SPACE，其實可以把第二個直接跟第一個做減法然後取ABS就可以了，但還算及格啦。

----
第二題:2575. Find the Divisibility Array of a String
實做複雜度:O(N)
使用技巧:字串轉數字&字元
https://leetcode.com/problems/find-the-divisibility-array-of-a-string/description/
這題是指要找到可以被m整除地位數並存成1，不能的話就要儲存成0。這題我在比賽的時候是沒想啦 但回頭來看應該要寫得真的不難。 我第一個解法是用Prefix去做，因為第一個測資是mod3所以我就想說，阿不就看餘數的mod做就好了結果第二個M是10就直接爆胎了。
但後來發現很直觀，直接一個一個做字串轉字元處理就好了。
程式如下:
```class Solution {
 public:
        vector<int> divisibilityArray(string word, int m) {
        vector<int> ans;
        long long t = 0;
        for(int i = 0; i < word.size(); ++i){
            t = (t * 10 + (word[i] - '0') ) % m;
            if(t == 0) {
                ans.push_back(1); 
            }
            else
            {
                 ans.push_back(0); 
            }
        }
        return ans;
  }
 };
 ```
 順便也提供第一個錯誤寫法，至少是沒有BUG拉
  ```
 class Solution {
public:
    vector<int> divisibilityArray(string word, int m) {
        //record number%m=k do prefix 0,0,2 ,4...
        vector<int> num;
        vector<int> ans;
    for(int i=0;i<word.size();i++)
    {
        if(i>=1)
        {
            num.push_back(word[i]%m+num[i-1]);
        }
        if(i==0)
        {
            num.push_back(word[i]%m);
        }
    }
        for(int i=0;i<num.size();i++)
        {
            if(num[i]%m==0)
            {
                ans.push_back(1);
            }
             if(num[i]%m != 0)
            {
                ans.push_back(0);
            }
        }
        return ans;    
    }
};
   ```
   
   ----
第三題:2576. Find the Maximum Number of Marked Indices
實做複雜度:O(N(logN))
使用技巧:雙指針
這題一開始我想錯了! 我本來以為是這樣子
2,3,4,5,6這四個數字
2可以跟6做搭配 3可以跟5做搭配，兩兩一組，看有幾組可以達成題目條件就做RETURN。然後我去跑Testcase就發現這樣其實跟答案的組數有一定的差距。
所以我就發現這樣不是最多的。
可以先看看我的code再來解釋:

  ```
  class Solution {
public:
    int maxNumOfMarkedIndices(vector<int>& nums) {
        int ans=0;
        sort(nums.begin(),nums.end());
        int left=0;
        int right=(nums.size()-1)/2+1;
        for(int i=0;i<nums.size()&&right<nums.size();i++)
        {
            if(2*nums[left]<=nums[right])
            {
                ans+=2;
                left++;
                right++;
            }
            else{
                    right++;
            }
        }
        return ans;
    }
};
  ```
  
 讓左指針從0開始，右邊的指針從中間開始(正中間)
 如果都可以配對這樣就會有最多組數，但如果沒有，就可以找出最佳解，因為小的那一邊最多就是走到正中間的前一個也就不會再走了(因為右邊最多走到最後一個就會停了，而且右邊一定會right++，所以每次右邊都會移動。
  
   






