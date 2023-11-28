---
title: 单调栈
tags: test
---

 
在全局变量和局部变量都声明的情况下，之会改变局部变量
```cpp
#include <iostream>
using namespace std;
int b;
void help(){
	cout<<b;
}
int main(){
	 int b;
	 cout<<b;//9
	 help();//0
}
```

###  Numbers of island
```cpp
#include <iostream>
using namespace std;
char a[350][350];
int b;
void check_island(int i,int j){
    if(i>=0 && j>=0 && i<b && j<b){
        if(a[i][j] == '0'){
            return;
        }
        a[i][j]='0';
        check_island(i-1,j);
        check_island(i+1,j);
        check_island(i,j-1);
        check_island(i,j+1);
    }
}
int main(){
    int res=0;
    cin>>b;
    for(int i = 0;i<b;i++){
        for(int j = 0; j<b;j++){
            cin>>a[i][j];
        }
    }
    for(int i = 0; i<b;i++){
        for(int j = 0; j<b;j++){
            if(a[i][j] == '1'){
                check_island(i,j);
                res++;
            }
        }
    }
    cout<<res;
}
```

### LeetCode  [739. Daily Temperatures](https://leetcode.cn/problems/daily-temperatures/)
```cpp

#include <iostream>
using namespace std;
int main(){
    int a[100000];
    int b;
    int res = 0;
    cin>>b;
    for(int i = 0;i< b;i++){
        cin>>a[i];
    }
    
    for(int i = 0;i<b-1;i++){
        for(int j = i;j<b;j++){
            if(a[i]<a[j]){
                cout<<res<<" ";
                break;
            }
            else{
                res++;

            }
        }
        res = 0;
    }
    cout<<0;
}
```

#### 单调递减栈
```cpp

#include <iostream>
#include <stack>
using namespace std;
stack<int> sta;
int main(){
        int a[100000];
        int b;
        int res[100];
        cin>>b;
        for(int i = 0;i< b;i++){
            cin>>a[i];
        }
    sta.push(0);
    for(int i=1; i<b;i++){
        if(a[sta.top()]>=a[i]){//单调递减栈顶需要比放进来的数大
            sta.push(i);
        }
        else{
            while(!sta.empty() && a[sta.top()]<a[i]){
                //sta.pop();
                res[sta.top()] = i-sta.top();
                sta.pop();
            }
            sta.push(i);
        }
    }
    for(int i = 0; i<=b;i++){
        cout<<res[i];
    }
    
}
```



  