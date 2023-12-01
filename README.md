<h3 align="center">算法基础课</h3>

## 1. 基础算法
### 1. 前缀和与差分
#### 1. 前缀和

要求：有数组a[]，求前i项和，a[0]+a[1]+a[2]....a[n]

思想：建立求和数组S[n],S[i]=a[0]+.....a[n]=S[i-1]+a[i]

例题：输入一个长度为 n的整数序列。接下来再输入 m 个询问，每个询问输入一对 l,r

对于每个询问，输出原序列中从第 l个数到第 r个数的和。
~~~c
#include<iostream>
using namespace std;
const int N=100000;
int main(){
    int a[N],S[N];
    int m,n;
    cin>>n>>m;
    for(int i=1;i<=n;i++)cin>>a[i];
    for(int i=1;i<=n;i++)S[i]=S[i-1]+a[i];
    while(m--){
        int l,r;
        cin>>l>>r;
        cout<<S[r]-S[l-1]<<endl;
    }
    return 0;
}
~~~
输入：
~~~
5 3
2 1 3 6 4
1 2
1 3
2 4
~~~               
输出：
~~~c
3
6        
10
~~~

#### 2. 子矩阵的和
