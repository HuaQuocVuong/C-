Kiểu Pair (ĐÔI)
pair nằm trong thư viện "utility" được sử dụng để kết hợp 2 kiểu dữ liệu với nhau, 
nó cung cấp cách lưu trữ 2 giá trị đi kèm nhau nhưng chỉ sử dụng 1 biến.

Nhìn chung pair giúp lưu trữ dữ liệu theo cặp và có những đặc điểm sau : 
•	Phần tử thứ nhất của pair được gọi là first, phần tử thứ 2 của pair được gọi là second.
•	Bạn có thể so sánh, gán, copy pair như kiểu dữ liệu bạn thường gặp
•	Để truy cập vào phần tử thứ nhất và thứ 2 trong pair ta sử dụng toán tử dấu chấm.

----------------------------------------------------------------------------
//Cách 1: first seconds là mặc định.
pair <first_data_type, second_data_type> pair_name;

//Cách 2 : Giá trị của first là value1, second là value2
pair <first_data_type, second_data_type> pair_name = make_pair(value1, value2)

//Cách 3 : Giá trị của first là value1, second là value2
pair <first_data_type, second_data_type> pair_name(value1, value2)

//Cách 4 : Giá trị của first là value1, second là value2
pair <first_data_type, second_data_type> pair_name = {value1, value2}
----------------------------------------------------------------------------

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

//Vi du 2: pair long nhau

#include <iostream>
#include <utility>

using namespace std;

int main() {

	int x, y, z;
	cout << "Nhap so nguyen x, y, z: ";
	cin >> x >> y >> z;

	//pair < kieu_du_lieu_1, pair < kieu_du_lieu_2 , kieu_du_lieu_3> > ten_ham = make_pair(x, (make_pair (y, z)));
	pair <int, pair<double, char>> a = make_pair(x, (make_pair(y, z)));

	//pair <[first]_, pai<[second.first], [second.seccond]>>
	cout << a.first << endl;	//first: Phan tu thu nhat cua pair
	cout << a.second.first << " " << a.second.second << endl;	//second.first: phan tu thu 2 //scond.second: phan tu thu 3

	int x1, x2, x3, x4;
	cout << "Nhap so nguyen x1, x2, x3, x4: ";
	cin >> x1 >> x2 >> x3;

	//pair<pair<kieu_du_lieu_1, kieu_du_lieu_2>, pair<kieu_du_lieu_3, kieu_du_lieu_4>> ten_ham = { {x1, x2}, {x3,x4} };
	pair<pair<int, int>, pair<int, int>> b = { {x1, x2}, {x3, x4} };


	//pair < pair<[first.first], [first.second]>, pair<[second.first], [second. second]> >
	cout << b.first.first << " " << b.first.second << endl; 
	cout << b.second.first << " " << b.second.second << endl;
}

 	 a
        /  \
   first   second
   (int)   (pair)
           /    \
       first   second
      (double) (chart)

             b
           /   \
      first    second
     (pair)     (pair)
     /   \       /   \
(int)   (int)  (int)  (int)


//Vi du 1: toan gan se gan gtri cuaa first va second cua 2 pair cho nhau
//string - chuoi ky tu

----------------------------------------------------------------------------
pair<data_type_1, data_type_2> result = (value_1, value_2);
cout << result.first << "  " << result.second << endl;

//first = value_1
//second = value_2
----------------------------------------------------------------------------

#include <iostream>
#include <utility>
using namespace std;

int main() {

	string x1;
	cout << "Nhap ky tu x1: ";
	cin >> x1; //ABCD
 
	int x2;
	cout << "Nhap so nguyen x2: ";
	cin >> x2;	//1234

	pair<string, int> p1 = make_pair(x1, x2);	//x1 = first //x2 = second	
	pair<string, int> p2 = p1;	
	//Gan p2 = P1  
	cout << p1.first << " " << p1.second << endl;
	cout << p2.first << " " << p2.second << endl;

	cout << p1.first << " " << p2.second << endl;	
	cout << p2.first << " " << p2.second << endl;
	
	//Mac dinh first = ABCD// second = 1234
	return 0;
}


//vi du 2: so sanh 2 pair 
//so sanh 2 gia tri first sau do so sanh second

---------------------------------------------------------------
pair<data_type_1, data_type_2> compare = {value_1, value_2};
cout << boolalpha << (value_1 ... value_2) << endl;

//true -> true
//false -> false
---------------------------------------------------------------

#include <iostream>
#include <utility>
using namespace std;

int main() {

	int x1, x2;
	cout << "Nhap so nguyen x1: ";
	cin >> x1;	//1
	cout << "Nhap so nguyen x2: ";
	cin >> x2;	//2

	//compare : so sanh
	pair<int, int> compare = { x1, x2 };

	cout << boolalpha << (x1 == x2) << endl;	// ==	(false)
	cout << boolalpha << (x1 != x2) << endl;	// !=	(true)	
	cout << boolalpha << (x1 > x2) << endl;		// >	(false)
	cout << boolalpha << (x1 < x2) << endl;		// <	(true)
}



//vi du 3: swap 2 pair voi nhau bang ham swap
---------------------------------------------------------------
.....
pair<data_type_1, data_type_2> variable_1 = {value_1, value_2};
pair<data_type_3, data_type_4> variable_2 = {value_3, value_4};

variable_1.swap(variable_2);

cout << variable_1.value_1 << " " << variable_1.value_2 << endl;	
// value_1 -> value 3; value_2 -> value_4

cout << variable_2.value_3 << " " << variable_2.va;ue_4 << endl;	
// value_2 -> value_1; value_4 -> value_2
---------------------------------------------------------------
#include <iostream>
#include <utility>

using namespace std;

int main() {
	int x1, x2;
	cout << "Nhap so nguyen x1, x2: ";
	cin >> x1 >> x2;	//x1 = 1 //x2 = 2
	int x3, x4;
	cout << "Nhap so nguyen x3, x4: ";
	cin >> x3 >> x4;	//x1 = 3 //x3 = 4

	pair<int, int> p1 = { x1, x2 };
	pair<int, int> p2 = { x3, x4 };

	cout << "before \n";
	cout << "p1(before) = {" << p1.first << "," << p2.second << "}" << endl;	//p1.first = 1, p1.second = 2
	cout << "p2(before) = {" << p2.first << "," << p2.second << "}" << endl;	//p2.first = 3, p2.second = 4

	p1.swap(p2);	//Gan p1 cho p2 (Hoan doi gia tri)
	cout << "swap after \n";	
	cout << "p1(after) = " << p1.first << "," << p1.second << "}" << endl;	//3 4
	cout << "p2(after) = " << p2.first << "," << p2.second << "}" << endl;	//1 2

	return 0;
}

1. Toán tử gán
- Toán tử gán dấu ( = ) được sử dụng trong các bài khi ta muốn gán giá trị cho biến
- Syntax (Cú pháp): x = y
- Meaning (Ý nghĩa): assingn x value to y value.

---------------------------------------------------------------
int x = value_x

int y = x;	//y = value_x
cout << "Value y = " << y <<  endl; //y = value x
---------------------------------------------------------------
#include <iostream>
using namespace std;

int main() {
	int x;
	cout << "Enter x value: ";
	cin >> x;

	//x value assigning to y value
	int y = x;
	cout << "x value = " << x << " before assigning to y value, y value = " << y << endl;

	return 0;
}

2. Toán tử toán học
   a. + (addition)
   b. - (subtraction)
   c. * (multiplication)
   d. / (division)
   e. % (modulus operator)

#include <iostream>
#include <math.h>

using namespace std;

int main() {

	int length, width;
	cout << "Enter length: ";
	cin >> length;
	cout << "Enter width: ";
	cin >> width;

	//perimeter of rectangle equal two multiply by (length plus width)
	int perimeter_of_rectangle = 2*(length + width);
	cout << "Perimeter of rectangle equal: " << perimeter_of_rectangle << endl;

	int acreage_of_rectangle = length * width;
	cout << "acreage of rectangle equal " << acreage_of_rectangle << endl;


	int dai, rong;
	cout << "Nhap chieu dai, rong: ";
	cin >> dai >> rong;
	int chuvi = 2 * (dai + rong);
	int dientich = dai * rong;
	cout << "Chu vi hinh chu nhat la: " << chuvi << endl;
	cout << "Dien tich hinh chu nhat la: " << dientich << endl;
	return 0;

}

//Ví dụ 2: tính bán kính và in kết quả số thập phân
---------------------------------------------------------------
...
#include <iomanip>
...
cout << fixed << setprecision(yy) << ...  << endl;	/output xx.yy
---------------------------------------------------------------
//Circle
#include <iostream>
#include <iomanip>

using namespace std;

int main() {

	double R;
	cout << "Enter R = ";
	cin >> R;	//R = 10
 
	//C = 2*Pi*R
	double C = 2 * 3.1415 * R;
	//S = Pi*R*R
	double S = 3.1415 * R * R;

	cout << "C = " << fixed << setprecision(4) << C << endl;	//62.8300
	cout << "S = " << fixed << setprecision(4) << S << endl;	//314.1500

	return 0;
}


//Vi du: phep chia nguyen

#include <iostream>
#include <iomanip>
using namespace std;

int main() {

	int x1, x2;
	int y1, y2;
	cout << "Enter x1, x2: ";
	cin >> x1 >> x2;	//4 2
	cout << "Enter y1, y2: ";
	cin >> y1 >> y2;	//1	2

	int division_1 = x1 / x2;	//4 / 2 = 2
	double division_2 = double(y1) / y2;	//1 / 2 = 0.50

	cout << "x1 / x2 = " << division_1 << endl;		//2
	cout << fixed << setprecision(2) << "y1 / y2 = " << division_2 << endl;		//0.50

	return 0;

}

Ví dụ 4: Phép chia muốn lấy phần thập phân có 2 cách xử lý
1. Ép kiểu số chia hoặc bị chia sang số thực.
2. Nhân só bị chia với 0.1, ngầm biến số bị chia thành số thực.


#include <iostream>
#include <iomanip>
using namespace std;

int main() {

	//Cach 1: ep kieu sang so thuc
	int x1, x2;
	cout << "Enter x1, x2: ";
	cin >> x1 >> x2;	//1 2
	
	float division_1 = (float)x1 / x2; // 1 / 2 = 0
	cout << fixed << setprecision(2) << "x1 / x2 = " << division_1 << endl;	//0.50
	

	//Cach 2: Nhan so bi chia voi 1.0

	int x3, x4;
	cout << "Enter x3, x4: ";
	cin >> x3 >> x4;	//1 2

	float division_2 = 1.0 * x3 / x4;	//1.0 * 1 / 2	= 0
	cout << fixed << setprecision(2) << "x3 / x4 = " << division_2 << endl;		//0.50



	return 0;

}

_Nhan hai so bi tran du lieu_

//Kieu [int]
//Giá trị nhỏ nhất : -2, 147, 483, 648 (−2^31)
//Giá trị lớn nhất : 2, 147, 483, 647 (2^31 − 1)

//Kieu [long long]
//Giá trị nhỏ nhất : -9, 223, 372, 036, 854, 775, 808 (− 2^63)
//Giá trị lớn nhất : 9, 223, 372, 036, 854, 775, 807 (2^63 − 1)

#include <iostream>
#include <iomanip>
using namespace std;

int main() {
	int x, y;	//data_type_int
	cout << "Enter x, y: ";
	cin >> x >> y;	//x = 10^6 = //y = 10^6

	long long tich_1 = x * y;
	cout << "(1) x * y = " << tich_1 << endl;	// FALSE: tich_1 = -727379968
-----------------------------------------------------------------------------------------------------
//ep kieu: <higher_data_type> <variable_name> = (hyger_data_type) <vale_1> * <value_2>;
-----------------------------------------------------------------------------------------------------
	long long tich_2 = (long long)x * y;
	cout << "(2) x * y = " << tich_2 << endl;	//TRUE tich_2 = 1000000000000
 
-----------------------------------------------------------------------------------------------------
//Nhan voi 1ll: <higher_data_type> <variable_name> = 1ll * <vale_1> * <value_2>;
 -----------------------------------------------------------------------------------------------------
	long long tich_3 = 1ll * x * y;
	cout << "(3) x * y = " << tich_3 << endl;	//TRUE tich_3 = 1000000000000

	return 0;
}

-------------------------------------------------
_Toan tu gan_
-------------------------------------------------
+=	|	 x = x + y	|	x += y

-=	|	 x = x - y	|	x -= y
	
*=	|	 x = x * y	|	x *= y

/=	|	 x = x / y	|	x /= y

%=	|	 x = x % y	|	x %= y
--------------------------------------------------


-------------------------------------------------
_Toan tu so sanh_
-------------------------------------------------
>	|	a > b

>=	|	a >= b

<	|	a < b

<=	| 	a <= b

!=	| 	a != b

==	|	a == b
-------------------------------------------------

#include <iostream>
#include <iomanip>

int main() {
	int x, y;
	std::cout << "Enter a, b: ";
	std::cin >> x >> y;	// x = 1; y =2
----------------------------------------------------------------------
//cout << boolalpha << ( <Value_1> <Comparison> <value_2> ) << endl;
----------------------------------------------------------------------
	//no namespace

	std::cout << std::boolalpha << (x < y) << std::endl;	//True
	std::cout << std::boolalpha << (x <= y) << std::endl;	//True

	std::cout << std::boolalpha << (x > y) << std::endl;	//False
	std::cout << std::boolalpha << (x >= y) << std::endl;	//False

	std::cout << std::boolalpha << (x != y) << std::endl;	//True
	std::cout << std::boolalpha << (x == y) << std::endl;	//false
}

-------------------------------------------------------
_Toan tu logic_	
(a = 1; b = 2)
-------------------------------------------------------
&&	|	(a < b && a = a )	|	True

||	|	(a > b || a = a )	|	True

!	|	!(a == a)		| 	False
-------------------------------------------------------


