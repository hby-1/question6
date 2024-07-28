# 复写零

给你一个长度固定的整数数组 arr ，请你将该数组中出现的每个零都复写一遍，并将其余的元素向右平移。

注意：请不要在超过该数组长度的位置写入元素。请对输入的数组 就地 进行上述修改，不要从函数返回任何东西。

## 示例 ：
>### 输入：
>[1,0,2,3,0,4,5,0]
>### 输出：
>[1,0,0,2,3,0,0,4]
>### 解释：
>调用函数后，输入的数组将被修改为：[1,0,0,2,3,0,0,4]

## 代码：

1.

    public class Solution {
        public void DuplicateZeros(int[] arr) {
            for(int i=0;i<arr.Length;i++){
                if(arr[i]==0){
                    if(i<arr.Length-2){
                        for(int n=arr.Length-1;n>i+1;n--){
                            arr[n]=arr[n-1];
                        }
                        arr[i+1]=0;
                        i++; 
                        continue;                  
                    }
                    if(i==arr.Length-2){
                        arr[i+1]=0;
                    }                
                }
            }
        }
    }

2.

    public class Solution {
        public void DuplicateZeros(int[] arr) 
        {
            int n = arr.Length;
            for (int i = 0; i < n; i++)
            {
                if (arr[i] == 0)
                {
                    for (int j = n - 1; j > i; j--)
                    {
                        arr[j] = arr[j - 1];
                    }
                    if (i + 1 < n)
                    {
                        arr[i + 1] = 0;
                    }
                    i++; // skip next element as it is duplicate of current
                }
            }
        }
    }

3.

    public class Solution {
        public void DuplicateZeros(int[] arr) {
            int n = arr.Length;
            int fast = 0, slow = 0;
            while (fast < n) {
                if (arr[slow] == 0) {
                    fast += 2;
                } else {
                    fast++;
                }
                slow++;
            }
            if (fast > n) {
                slow--;
                fast -= 2;
                arr[fast] = 0;
            }
            while (fast > slow) {
                fast--;
                slow--;
                int curr = arr[slow];
                arr[fast] = curr;
                if (curr == 0) {
                    fast--;
                    arr[fast] = curr;
                }
            }
        }
    }
