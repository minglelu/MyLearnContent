# 本文记录在ACM竞赛中的笔记
  
  
  
## 差分数组
差分数组的主要用途是**频繁对原始数组的某个区间的元素进行增减**

比如说有个数组`nums`,然后要求对区间`nums[2..6]`全部加一...  
第一种用for循环,但时间复杂度是O(N)  
第二种先对`nums`数组构造一个`diff`差分数组,`diff[i]`就是`nums[i]`和`nums[i-1]`之差  
```java
int[] diff = new int[nums.length];
//构造差分数组
diff[0] = nums[0];
for(int i = 1; i < nums.length; i++){
    diff[i] = nums[i] - nums[i-1];
}
```
通过这个代码可以反推出原始数组`nums`  
```java
int[] res = new int[diff.length];
//根据差分数组构造结果数组
res[0] = diff[0];
for (int i = 1; i < diff.length; i++){
res[i] = res[i-1] + diff[i];
}
```
如果要对数组`nums[i..j]`的元素全部加1,那么只需要让`diff[i] += 1`,然后再让`diff[j+1] -= 1`即可  
只要花费 O(1) 的时间修改 diff 数组，就相当于给 nums 的整个区间做了修改。多次修改 diff，然后通过 diff 数组反推，即可得到 nums 修改后的结果
```c++
//创建一个全为0数组，被移走就是加1，那么正的数就是被移走的，区间加减用差分
//变量定义
int s[100001],m,l,start,end,ans; //s差分数组
//main 函数里
cin >> l >> m;
for(int i = 1; i <= m; i++){
 cin >> start >> end;
 s[start]++,s[end + 1]--;
}
if(!s[0]) ans++;
for(int i = 1; i <= l; i++){
 s[i] += s[i-1];
 if(!s[i]){
   ans++;
 }
}
cout << ans;







