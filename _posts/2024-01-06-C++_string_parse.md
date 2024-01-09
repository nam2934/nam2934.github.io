---
title:  "[C++] Split String"
excerpt: ""

categories:
  - Algorithm
tags:
  - [algorithm, cpp, string]

breadcrumb: true
toc: true
toc_sticky: true
 
date: 2024-01-06
last_modified_at: 2024-01-06
---
<br>

# About sstream
문자열이 주어졌을 때, 공백이나 특정 문자를 기준으로 split 하는 것이 python에서는 `split()`으로 해결되지만, C++ 에서는 한줄로 해결되는 마땅한 메소드가 없어 sstream이 그 중에서 가장 간단하고 적합하다.<br>


## Header
```cpp
#include<sstream>
```
sstream 헤더에 포함되어 있다.

## 예제 코드

```cpp
#include<iostream>
#include<string>
#include<sstream>
#include<vector>

#define N 5

using namespace std;

int main(){
    string rs[3];
    string s = "123 456 789";
    string s_del = "123|456|789";
    vector<string> v;

    /* 
        Empty constructor & using str() member function
        iss.str(s) - sets str as the contents of the stream, discarding any previous contents
        iss.str() - returns a string object with a copy of the current contents of the stream
    */
    #if N == 1
        istringstream iss;
        iss.str(s);
        for(int i=0; i<3; i++){
            iss >> rs[i];
        }
        for(auto i : rs){
            cout << i << endl;
        }
    /* 
        Initialization constructor
        istringstream iss(s) construct an istreamstring object to copy of given string s
    */        
    #elif N == 2
        istringstream iss(s);
        for(int i=0; i<3; i++){
            iss >> rs[i];
        }
        for(auto i : rs){
            cout << i << endl;
        }       
    /*
        Initialization constructor with non-determined string size
        while(iss >> temp_str) - iterate until the end of stream.
    */         
    #elif N == 3
        istringstream iss(s);
        string temp_str;
        while(iss >> temp_str){
            v.push_back(temp_str);
        }
        for(auto i : v){
            cout << i << endl;
        }                
    /*
        more simple example for using vector
    */
    #elif N == 4
        istringstream iss(s);
        v = vector<string>(istream_iterator<string>(iss), istream_iterator<string>());
        for(auto i : v){
            cout << i << endl;
        }                
    /*
        another delimiter(e.g., '|')
    */
    #elif N == 5
        istringstream iss(s_del);
        string temp_str;
        while(getline(iss, temp_str, '|')){
            v.push_back(temp_str);
        }
        for(auto i : v){
            cout << i << endl;
        }
    #endif
}
```

String을 vector에 담아두는 경우가 추후 processing 하기에 유리하기 때문에 N이 4인 경우와 5인 경우를 외워두면 편리할 것 같다.<br>
N이 4인 경우, 주어진 vector v 에 s를 whitespace로 split 하여 넣는 코드이고<br>
N이 5인 경우, 특정 delimiter로 split 하는 코드이다.<br>

<br>



