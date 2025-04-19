Kiểu Pair (ĐÔI)
pair nằm trong thư viện "utility" được sử dụng để kết hợp 2 kiểu dữ liệu với nhau, 
nó cung cấp cách lưu trữ 2 giá trị đi kèm nhau nhưng chỉ sử dụng 1 biến.

Nhìn chung pair giúp lưu trữ dữ liệu theo cặp và có những đặc điểm sau : 
•	Phần tử thứ nhất của pair được gọi là first, phần tử thứ 2 của pair được gọi là second.
•	Bạn có thể so sánh, gán, copy pair như kiểu dữ liệu bạn thường gặp
•	Để truy cập vào phần tử thứ nhất và thứ 2 trong pair ta sử dụng toán tử dấu chấm.

//Cách 1: first seconds là mặc định.
pair <first_data_type, second_data_type> pair_name;
//Cách 2 : Giá trị của first là value1, second là value2
pair <first_data_type, second_data_type> pair_name = make_pair(value1, value2)
//Cách 3 : Giá trị của first là value1, second là value2
pair <first_data_type, second_data_type> pair_name(value1, value2)
//Cách 4 : Giá trị của first là value1, second là value2
pair <first_data_type, second_data_type> pair_name = {value1, value2}

Thành phần first và second của pair có thể là các kiểu dữ liệu thường gặp như int, float, double, long long,char... 
hay cũng có thể chính là một pair khác. Ngoài ra nó còn có thể là các kiểu phức tạp hơn như string, vector<>, set, object... 
tuy nhiên nhưng kiến thức này bạn chưa gặp nên tạm thời bỏ qua.

vi du 1: khai bao pair

#include <iostream>
#include <utility>
using namespace std;
int main() {

	int x, y;
	cout << "Nhap so nguyen x, y: ";
 	cin >> x >> y;	//1 2

	double z, t;
	cout << "Nhap so thap phan z, t: ";
	cin >> z >> t;	//1.5 2.5

	char m, n;
	cout << "Nhap ky tu m, n: ";
	cin >> m >> n;	//A B


	pair <int, int> a = make_pair(x, y);
	cout << a.first << " " << a.second << endl;

	pair <double, double> b = { z, t };
	cout << b.first << " " << b.second << endl;

	pair <char, char> c(m, n);
	cout << c.first << " " << c.second << endl;
}



