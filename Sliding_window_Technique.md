# Sliding window Technique:-

<https://www.geeksforgeeks.org/window-sliding-technique/>



```
#include <iostream>
#include<bits/stdc++.h>
using namespace std;

// To execute C++, please define "int main()"
int slidingWindow(int a[], int n, int k, map<int,vector<int> > &m);
int main() {
  auto words = { "Hello, ", "World!", "\n" };
  for (const string& word : words) {
    cout << word;
  }
  vector<int> v;
  queue<int> q;
  q.push(1);
  q.push(2);
  q.push(3);
  q.push(4);
  cout<<q.front()<<endl;
   q.pop();
  cout<<q.back()<<endl;
  map<int,string> m;
  m[1]="one";
  m.insert(pair<int,string>(2,"two"));
  for(pair<int,string> p:m){
    cout<<"First: "<<p.first<<endl;
    cout<<"Second: "<<p.second<<endl;
  }
  unordered_map<int,string> um;
  um[5]="Five";
  um[6]="six";
  um[7]="Seven";
  for(pair<int,string> p:um){
    cout<<"First: "<<p.first<<endl;
    cout<<"Second: "<<p.second<<endl;
  }
  um.erase(7);
  for(pair<int,string> p:um){
    cout<<"First: "<<p.first<<endl;
    cout<<"Second: "<<p.second<<endl;
  }
  vector<string> v1;
  vector<string>::iterator it;
  it = v1.begin();
  v1.push_back("Hello");
  //it++;
  //it++;
  //v1.insert(it,1,"Hi");
  v1.push_back("Fine");
  cout<<v1.front()<<endl;
  v1.erase(v1.begin()+1);
  for(string s:v1){
    cout<<s<<endl;
  }
  int slw[]={2,5,1,6,8,9};
  int len= sizeof(slw)/sizeof(slw[0]);
  map<int,vector<int> > slwm;
   slidingWindow(slw, len, 2, slwm);
    cout<<"Printing Sliding Window"<<endl;
  for(pair<int,vector<int>> p: slwm) {
    cout<<p.first<<":"<<"(";
    vector<int> v3 = p.second;
    cout<<"From "<<*(v3.begin());
    cout<<" To "<<*(v3.begin()+1);
    cout<<" Sum "<<*(v3.begin()+2) <<endl;
  }
  return 0;
}

int slidingWindow(int a[], int n, int k, map<int,vector<int> > &m){
  int sum = 0;
  //map<int,vector<int> > m;
  vector<int> v1;
  for( int i =0; i<k;i++){
    sum+=a[i];
  }
  v1.push_back(0);
  v1.push_back(k-1);
  v1.push_back(sum);
  m[0]=v1;
  for(int i=k;i<n;i++){
    sum+=a[i]-a[i-k];
    vector<int> v2;
    v2.push_back(i-k+1);
    v2.push_back(i);
    v2.push_back(sum);
    m[i-k+1]=v2;
  }
  //cout<<"Printing Sliding Window"<<endl;
  /*
  for(pair<int,vector<int>> p: m) {
    cout<<p.first<<":"<<"(";
    vector<int> v3 = p.second;
    cout<<"From "<<*(v3.begin());
    cout<<" To "<<*(v3.begin()+1);
    cout<<" Sum "<<*(v3.begin()+2) <<endl;
  } */
  return 0;
}
```

