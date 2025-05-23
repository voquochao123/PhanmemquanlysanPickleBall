# PhanmemquanlysanPickleBall
#include <iostream>
using namespace std;
struct San {
    int so_san;
    int loai_san;
    int trang_thai;
};
San dsSan[100];
int soLuongSan = 0;
void themSan() {
    cout << "Nhập số sân: ";
    cin >> dsSan[soLuongSan].so_san;
    cout << "Loại sân (1: Ngoài trời, 2: Trong nhà): ";
    cin >> dsSan[soLuongSan].loai_san;
    dsSan[soLuongSan].trang_thai = 1;
    soLuongSan++;
    cout << "Thêm sân thành công.\n";
}
void xoaSan() {
    cout << "Nhập số sân cần xóa: ";
    int soSanXoa;
    cin >> soSanXoa;
    for (int i = 0; i < soLuongSan; i++) {
        if (dsSan[i].so_san == soSanXoa) {
            for (int j = i; j < soLuongSan - 1; j++) {
                dsSan[j] = dsSan[j + 1];
            }
            soLuongSan--;
            cout << "Xóa sân thành công.\n";
            return;
        }
    }
    cout << "Không tìm thấy sân.\n";
}
void hienThiSan() {
    cout << "Danh sách sân:\n";
    for (int i = 0; i < soLuongSan; i++) {
        cout << "Sân " << dsSan[i].so_san
             << ", Loại: " << (dsSan[i].loai_san == 1 ? "Ngoài trời" : "Trong nhà")
             << ", Trạng thái: ";
        if (dsSan[i].trang_thai == 1) cout << "Trống\n";
        else if (dsSan[i].trang_thai == 2) cout << "Đang sử dụng\n";
        else cout << "Bảo trì\n";
    }
}
int main() {
    int choice;
    do {
        cout << "\n1. Thêm sân\n2. Xóa sân\n3. Hiển thị sân\n0. Thoát\nChọn: ";
        cin >> choice;
        if (choice == 1) themSan();
        else if (choice == 2) xoaSan();
        else if (choice == 3) hienThiSan();
    } while (choice != 0);
    return 0;
}

