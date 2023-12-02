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
要求：求一个矩阵a[][]的任意子矩阵的和
思想：建立求和数组是s[][],s[i][j]表示是a[0][0]+....a[i][j],则s[i][j]=s[i][j-1]+s[i-1][j]-s[i-1][j-1]+a[i][j];子矩阵的和可以表示为s[x2][y2]-s[x2][y1-1]-s[x1-1][y2]+s[x1-1][y1-1]
例题：输入一个n行m列的整数矩阵，再输入q个询问，每个询问包含四个整数 x1,y1,x2,y2，表示一个子矩阵的左上角坐标和右下角坐标。对于每个询问输出子矩阵中所有数的和。
~~~c
#include<iostream>
using namespace std;
const int N=1010;
int main(){
    int m,n,q;
    int a[N][N],s[N][N];
    cin>>n>>m>>q;
    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            cin>>a[i][j];
        }
    }
    for(int i=1;i<=n;i++){
        for(int j=1;j<=m;j++){
            s[i][j]=s[i-1][j]+s[i][j-1]-s[i-1][j-1]+a[i][j];
        }
    }
    
    while(q--){
        int x1,y1,x2,y2;
        cin>>x1>>y1>>x2>>y2;
        cout<<s[x2][y2]-s[x2][y1-1]-s[x1-1][y2]+s[x1-1][y1-1]<<endl;
        }
        return 0;
}
~~~
输入：
~~~c
3 4 3
1 7 2 4
3 6 2 8
2 1 2 3
1 1 2 2
2 1 3 4
1 3 3 4
~~~
输出:
~~~c
17
27
21
~~~



