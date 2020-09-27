# 2020.9.27————盛最多水的容器
## 题目
你 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

说明：你不能倾斜容器，且 n 的值至少为 2。
![](https://aliyun-lc-upload.oss-cn-hangzhou.aliyuncs.com/aliyun-lc-upload/uploads/2018/07/25/question_11.jpg)

图中垂直线代表输入数组 [1,8,6,2,5,4,8,3,7]。在此情况下，容器能够容纳水（表示为蓝色部分）的最大值为 49。

## 解题
### 解法一  暴力法
#### 语言
java
#### 思路
直接两次左右循环，查找最大值。
#### 代码
```java
public class Solution{
    public int maxArea(int[] height){
        int maxArea =0;
        for(int i=0;i<height.length;i++){
            for(int j=i+1;j<height.length;j++){
                maxArea = Math.max(maxArea,Math.min(height[i],height[j])*(j-i));
            }
        }
        return maxArea;
    }
}
```
### 解法二   双指针法
#### 语言
java
#### 思路
双指针算法，从两侧遍历，然后查找最大面积的左右。如果左小于右那就移动左边，反之移动右边
#### 代码
```java
class Solution {
    public int maxArea(int[] height) {
        int l = 0,r = height.length-1;
        int area=0;
        while(l<r){
            area = (Math.max(area,Math.min(height[l],height[r])*(r-l)));
            if(height[l]<=height[r]){
                ++l;
            }else{
                --r;
            }
        }
        return area;
    }
}
```
