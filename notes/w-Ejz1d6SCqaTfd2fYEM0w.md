```cpp=
#include <iostream>
#include <algorithm>
#include <cstdlib>
using namespace std;

struct Phanso {
    long long tu, mau;
};

// Ham nhap phan so
void Nhap(Phanso &x) {
    cout << "Nhap tu so: ";
    cin >> x.tu;
    cout << "Nhap mau so: ";
    cin >> x.mau;
}

// Ham xuat phan so
void Xuat(const Phanso &x) {
    if (x.mau == 0) {
        cout << "Khong ton tai phan so" << endl; 
    } else if (x.tu == 0) {
        cout << "Phan so sau khi rut gon: 0" << endl; 
    } else if (x.mau == 1) {
        cout << "Phan so sau khi rut gon: " << x.tu << endl; 
    } else {
        cout << "Phan so sau khi rut gon: " << x.tu << "/" << x.mau << endl; 
    }
}

// Ham rut gon phan so
void Rutgon(Phanso &x) {
    if (x.mau == 0) {
        return; 
    }

    if (x.mau < 0) { 
        x.tu = -x.tu; 
        x.mau = -x.mau; 
    }
// Hàm gcd() cho phép lấy ước chung lớn nhất của tử và mẫu
    int rutgon = __gcd(x.tu, x.mau); 
    x.tu /= rutgon;
    x.mau /= rutgon;
}

int main() {
    Phanso x;
    Nhap(x);
    Rutgon(x);
    Xuat(x);

    return 0;
}

```