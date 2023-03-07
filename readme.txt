A Thực hành
1.
#include <iostream>
using namespace std;
void truyenham(int *a){
    cout<<a<<endl;
};
int main(){
    int a[2];
    a[0]=2;
    cout<<&a<<endl<<&a[0]<<endl;
    truyenham(a);
}


Địa chỉ của con trỏ trong hàm giống địa chỉ con trỏ ngoài main


2. Không có lệnh kết thúc vòng lặp của đệ quy 
3. Lệnh lặp vô hạn vì N không thay đổi giá trị
4. Đệ quy tốn nhiều bộ nhớ vì nạp chồng stack
5.
#include <iostream>
using namespace std;
long F(int n) { 
   if (n == 0) return 0; 
   if (n == 1) return 1; 
   return F(n-1) + F(n-2); 
}
int main(){
    cout<<F(40);
}
--> Time :  0.701 s


#include <iostream>
using namespace std;

int main(){
    int x0=0;
    int x1=1;
    int x2=0;
    long s=0;
    for(int i=0;i<40;i++){
        x2=s;
        s=x0+x1;
        x0=x2;
        x1=s;
    }
    cout<<s;
}

--> Time: 0.045 s
--> nhanh hơn vì không mất công giải phóng stack


6.
#include <iostream>
using namespace std;

long dequy(long n){
    if(n==1) return 1;
    return n*dequy(n-1);
}
int main(){
    cout<<dequy(100000)<<endl;
}

den 100000 thì overstack
 7.
#include <iostream>
using namespace std;
void swapp(string&s,int &lo, int&hi){
    char x=s[lo];
    s[lo]=s[hi];
    s[hi]=x;
    return;
}
void permutation(string &s,int lo, int hi){
    if(lo==hi) {
        cout<<s<<" ";
        return;
    }
    for(int i=lo;i<=hi;i++){
        swapp(s,lo,i);
        permutation(s,lo+1,hi);
        swapp(s,lo,i);
    }
}
int main(){
    string s;
    cin>>s;
    int n=s.size()-1;
    permutation(s,0,n);
}
8.
#include <bits/stdc++.h>
using namespace std;

int n;
bool member[1001];
void combination(int k) {
    if (k<1) {
        for(int i=1;i<=n;i++){
            if(member[i]==true){
                cout<<i;
            }
        }
        cout<<endl;
        return;
    }
    member[k] = true;
    combination(k-1);
    member[k] = false;
    combination(k-1);
}
int main(){
    cin>>n;
    memset(member,false, sizeof(member));
    combination(n);
}


// them ngoac
#include <bits/stdc++.h>
using namespace std;

int n;
bool member[1001];
void combination(int k) {
    if (k<1) {
        cout<<"[";
        bool check=false;
        for(int i=1;i<=n;i++){
            if(member[i]==true){
                if(check==false) check=true;
                else cout<<",";
                cout<<i;
            }
        }
        cout<<"]"<<endl;
        return;
    }
    member[k] = true;
    combination(k-1);
    member[k] = false;
    combination(k-1);
}
int main(){
    cin>>n;
    memset(member,false, sizeof(member));
    combination(n);
}




