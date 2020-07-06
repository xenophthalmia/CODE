//C_ARRAY01
#include<iostream>
#include<string>
#include<sstream>
using namespace std;

int main()
{
 int arr[100] = {0};
 int i = 0,j;
 string str;
 getline(cin,str);
 stringstream ss(str);
 while (ss >> arr[i++])//將讀到的資料寫入
 {
  
 }
 for (j = i - 2;j >= 0; j--)//反轉並印出
 {
  if (j < i - 2)
  cout << " ";
  cout << arr[j];
 }
 cout << endl;
 return 0;
}


//C_ARRAY02
#include<iostream>
#include<string>
#include<sstream>
using namespace std;

int main()
{
 int arr[6] = {0};//array最多6個
 int i = 0,j;
 string str;
 getline(cin,str);
 stringstream ss(str);
 while (ss >> arr[i++])
 {
  
 }
 for (j = i - 2;j >= 0; j--)
 {
  if (j < i - 2)
  cout << " ";
  cout << arr[j];
 }
 cout << endl;
 return 0;
}

//C_ARRAY03
#include<iostream>
using namespace std;

int main()
{
 int sum = 0;
 int arr[100];
 for (int i = 0;i < 6; i++)
  cin >> arr[i];
 for (int j = 0;j < 6; j++)
  sum += arr[j] * arr[j] * arr[j];//立方和
 cout << sum << endl;
 return 0;
}

//C_ARRAY05
#include <iostream>
using namespace std;

int main()
{
 int num,s,d,max;
 //s:發車時間 d :distance
 int time[100] = {0};
 cin >> num;
 max = 0;
 for (int i = 0;i < num; i++)
 {
  cin >> s >> d;
  for (int j = s;j < d; j++)
  {
   time[j]++;
  }
  for (int k = 0;k < 25; k++)
  {
   if (time[k] > max)
   max = time[k];//比對max是否為應派出最少車輛數，若人數超過車子能負荷的人數，應多派一台，故多寫這做比對
  }
 }
 cout << max << endl;
 return 0;
}

//C_ARRAY08
#include<iostream>
#include<string>
using namespace std;

int main()
{
 int num = 0, l = 0, prime = 0, check = 0;
 string s;
 getline(cin, s);
 if (s.length() >= 2)
 {
  for (int k = s.length(); k >= 2; k--)
  {
   for (int i = 0; i <= s.length() - k; i++)
   {
    num = 0;
    check = 0;
    for (int j = i; j < i + k; j++)
    {
     l = 1;
     for (int x = j - i + 1; x < k; x++)
      l *= 10;
     num += (s[j] - '0') * l;
    }
    for (int j = 2; j * j <= num; j++)
    {
     if (j % 2 == 0 && j > 2)
      continue;
     if (num % j == 0)
     {
      check = 1;
      break;
     }
    }
    if (check == 0)
    {
     if (num > prime)
      prime = num;
    }
   }
  }
 }
 for (int i = 0; i < s.length(); i++)
 {
  check = 0;
  num = s[i] - '0';
  for (int j = 2; j < num; j++)
  {
   if (num % j == 0)
   {
    check = 1;
    break;
   }
  }
  if (check == 0)
  {
   if (num > prime)
    prime = num;
  }
 }
 if (prime == 0)
  cout << "No prime found" << endl;
 else
  cout << prime << endl;
 return 0;
}

//C_ARRAY09
#include<iostream>
#include<string>
#include<sstream>
using namespace std;

void replace(string &s)//remove dot
{
 int i = 0;
 while (i < s.length())
 {
  if (s[i] == ',')
   s[i] = ' ';
  i++;
 }
}

int main()
{
 int x = 0, MAX = 0, MIN = 0, largest = 1, ml = 1, nl = 1;
 int n[7] = { 0 };
 string s;
 getline(cin, s);
 replace(s);
 stringstream ss(s);
 while (ss >> n[x])
 {
  x++;
  largest *= 10;
 }
 for (int i = 0; i < x - 1; i++)
 {
  for (int j = i; j < x; j++)
  {
   if (n[i] > n[j])
   {
    int tmp = n[i];
    n[i] = n[j];
    n[j] = tmp;//bubble sort 排序各字
   }
  }
 }
 for (int i = 0; i < x; i++)
 {
  ml = 1;
  nl = largest / 10;
  for (int j = 0; j < i; j++)
  {
   ml *= 10;
   nl /= 10;
  }
  MAX += n[i] * ml;
  MIN += n[i] * nl;
 }
 cout << MAX - MIN << endl;
 return 0;
}

//C_ARRAY20
#include<iostream>
using namespace std;

int main()
{
 int n, ans = 0;
 int count[129] = { 0 };
 cin >> n;
 int *arr = new int[n];
 for (int i = 0; i < n; i++)
  cin >> arr[i];
 for (int i = 0; i < n; i++)
 {
  for (int j = 0; j < n; j++)
  {
   if (arr[j] == arr[i])
    count[arr[j]]++;
   if (count[arr[j]] > 1)
   {
    ans = 1;
    break;
   }
  }
  if (ans == 1)
   break;
 }
 if (ans == 0)
  cout << "1" << endl;
 else
  cout << "0" << endl;
 return 0;
}

//C_ARRAY22
#include<iostream>
#include<string>
using namespace std;

int main()
{
 int arr[26] = { 0 };
 string s;
 getline(cin, s);
 for (int i = 0; i < s.length(); i++)
 {
  if (s[i] >= 'a' && s[i] <= 'z')
   s[i] -= 32;    //全部轉大寫
  if ((s[i] >= 'a' && s[i] <= 'z') || (s[i] >= 'A' && s[i] <= 'Z'))
   arr[s[i] - 'A']++;
 }
 for (int i = 0; i < 26; i++)
 {
  if (i > 0)
   cout << " ";
  cout << arr[i];
 }
 cout << endl;
 return 0;
}

//C_ARRAY25
#include<iostream>
#include<string>
using namespace std;

int main()
{
 int cnt = 0, x = 0;
 int num[100] = { 0 }, times[100] = { 0 };
 string s;
 getline(cin, s);
 for (int i = 0; i < s.length(); i++)
 {
  cnt = 1;
  if (s[i] != ' ')
  {
   for (int j = 0; j < s.length(); j++)
   {
    if (i != j && s[j] == s[i])
    {
     cnt++;
     s[j] = ' ';
    }
   }
   num[x] = s[i];
   times[x] = cnt;
   s[i] = ' ';
   x++;
  }
 }
 for (int i = 0; i < x - 1; i++)
 {
  for (int j = i + 1; j < x; j++)
  {
   if (i != j && num[i] < num[j])
   {
    int tmp = num[i];
    num[i] = num[j];
    num[j] = tmp;
    int temp = times[i];
    times[i] = times[j];
    times[j] = temp;
   }//用兩個bubble sort分別對次數跟ASCII 做排序
  }
 }
 for (int i = 0; i < x; i++)
  cout << num[i] << " " << times[i] << endl;
 return 0;
}

//基礎01
#include<iostream>
#include<string>
using namespace std;

int main()
{
	string num[10][5];

	num[0][0] = "*****";
	num[0][1] = "*   *";
	num[0][2] = "*   *";
	num[0][3] = "*   *";
	num[0][4] = "*****";

	num[1][0] = "    *";
	num[1][1] = "    *";
	num[1][2] = "    *";
	num[1][3] = "    *";
	num[1][4] = "    *";

	num[2][0] = "*****";
	num[2][1] = "    *";
	num[2][2] = "*****";
	num[2][3] = "*    ";
	num[2][4] = "*****";

	num[3][0] = "*****";
	num[3][1] = "    *";
	num[3][2] = "*****";
	num[3][3] = "    *";
	num[3][4] = "*****";

	num[4][0] = "*   *";
	num[4][1] = "*   *";
	num[4][2] = "*****";
	num[4][3] = "    *";
	num[4][4] = "    *";

	num[5][0] = "*****";
	num[5][1] = "*    ";
	num[5][2] = "*****";
	num[5][3] = "    *";
	num[5][4] = "*****";

	num[6][0] = "*****";
	num[6][1] = "*    ";
	num[6][2] = "*****";
	num[6][3] = "*   *";
	num[6][4] = "*****";

	num[7][0] = "*****";
	num[7][1] = "    *";
	num[7][2] = "    *";
	num[7][3] = "    *";
	num[7][4] = "    *";

	num[8][0] = "*****";
	num[8][1] = "*   *";
	num[8][2] = "*****";
	num[8][3] = "*   *";
	num[8][4] = "*****";

	num[9][0] = "*****";
	num[9][1] = "*   *";
	num[9][2] = "*****";
	num[9][3] = "    *";
	num[9][4] = "    *";

	string s;
	while (cin >> s)
	{
		for (int i = 0; i < 5; i++)
		for (int j = 0; j < s.length(); j++)
		{
			if (j > 0)
				cout << " ";
			cout << num[s[j] - '0'][i];
			if(j == s.length() - 1)
				cout << endl;
		}
	}
	return 0;
}

//基礎02
#include <iostream>
#include <iomanip>
using namespace std;

int main ()
{
	int mi;
	double km;
	cin >> mi;
	km = mi * 1.6;
	cout << fixed << setprecision(1) << (double)km << endl;
	return 0;
}

//基礎03
#include <iostream>
#include <cmath>
using namespace std;
double Count(double X);
int main ()
{
	int X,Y,x,radius;
	cin >> X >> Y;
	x = X * X + Y * Y;
	radius = Count(x);
	if (radius <= 100)
	{cout << "inside" << endl;}
	else
	{cout << "outside" << endl;}
	return 0;
}
double Count(double x)
{return pow(x,1.0 / 2);}

//基礎04
#include <iostream>
using namespace std;

int main ()
{
	int a,b,c,d;
	cin >> a >> b ;//a點b分
	cin >> c >> d ;//c點d分
	
	int x,y;
	y = ((c - a) * 60 + d - b);
	//對各區間的值分別進行判定與加總
	if (y <= 120)
	{
		x = (y / 30) * 30;
	}
	else if (y > 120 && y <= 240)
	{
		x = 4 * 30 + ((y - 120) / 30) * 40;
	}
	else if (y > 240)
	{
		x = 4 * 30 + 4 * 40 + ((y - 240) / 30) * 60;
	}
	
	cout << x << endl;
	return 0;
}

//基礎05
#include <iostream>
using namespace std;

int main ()
{
	int i;
	int b0,b1,b2,b3,b4,b5,b6,b7;
	cin >> i;
	if (i > 0 && i <= 127)
	{	
	    b0 = i & 1;
	    b1 = (i >> 1) & 1;
	    b2 = (i >> 2) & 1;
	    b3 = (i >> 3) & 1;
	    b4 = (i >> 4) & 1;
	    b5 = (i >> 5) & 1;
	    b6 = (i >> 6) & 1;
	    b7 = (i >> 7) & 1;
	    cout << b7 << b6 << b5 << b4 << b3 << b2 << b1 << b0 << endl;
	}
	else if (i == 0)
	{
		cout << "00000000" << endl;
	}
	else if (i < 0 && i >= -128)
	{
		b0 = i & 1;
	    b1 = (i >> 1) & 1;
	    b2 = (i >> 2) & 1;
	    b3 = (i >> 3) & 1;
	    b4 = (i >> 4) & 1;
	    b5 = (i >> 5) & 1;
	    b6 = (i >> 6) & 1;
	    b7 = (i >> 7) & 1;
	    cout << b7 << b6 << b5 << b4 << b3 << b2 << b1 << b0 << endl;
	}
	return 0;
}

//基礎06
#include <iostream>
using namespace std;

int main ()
{
 int m;
 cin >> m;
 switch (m)
 {
  case 3:
  case 4:
  case 5:
   cout << "Spring" << endl;
   break;
  case 6:
  case 7:
  case 8:
   cout << "Summer" << endl;
      break;
  case 9:
  case 10:
  case 11:
   cout << "Autumn" << endl;
   break;
  case 12:
  case 1:
  case 2:
   cout << "Winter" << endl;
   break;
 }
 return 0;
}

//基礎07
#include <iostream>
using namespace std;

int main ()
{
	int n,a,b,c,d,sum,sum1;
	char k;
	sum = sum1 = 0;
	cin >> n;
	for (int i = 0;i < n; i++)
	{
		cin >> k;
		cin >> a >> b >> c >> d;
		if (k == '+')
		{
			sum = a + c;//實部相加
			sum1 = b + d;//虛部相加
			cout << sum << " " << sum1 << endl;
		}
		else if (k == '-')
		{
			sum = a - c;
			sum1 = b - d;
			cout << sum << " " << sum1 << endl;
		}
		else if (k == '*')
		{
			sum = a * c - b * d;
			sum1 = b * c + a * d;
			cout << sum << " " << sum1 << endl;
		}
		else if (k == '/')
		{
			sum = (a * c + b * d) / (c * c + d * d);
			sum1 = (b * c - a * d) / (c * c + d * d);
			cout << sum << " " << sum1 << endl;
		}
	}
	return 0;
}

//基礎08
#include <iostream>
using namespace std;

int main ()
{
	int n,a,prime;
	cin >> n;
	prime = 1;
	a = 2;
	while (a < n)
	{
		if (n % a == 0)
		{
			prime = 0;
		}
		a++;
	}
	if (prime == 1)
	{
		cout << "YES" << endl;
	}
	else
	{
		cout << "NO" << endl;
	}
	return 0;
}

//基礎09
#include <iostream>
using namespace std;

int main()
{
	int n,sum,i;
	i = 1;
	sum = 0;
	cin >> n;
	while (i <= n)
	{
		if (i % 3 == 0)
		{
			sum += i;
		}
		i++;
	}
	cout << sum << endl;
	return 0;
}

//基礎10
#include <iostream>
using namespace std;

int main ()
{
	int a,b;
	cin >> a >> b;
	
	while (a != 0 && b != 0)
	{
		if (a >= b)
		{
			a = a % b;
		}
		else
		{
			b = b % a;
		}
	}
	if (a >= b)
	{
		cout << a << endl;
	}
	else
	{
		cout << b << endl;
	}
	return 0;
}

//基礎11
#include <iostream>
using namespace std;

int main()
{
	int a,b,count;
	int *num;
	count = 0;
	cin >> a >> b;//行、列
	num = new int[a * b];
	for (int i = 0;i < (a * b); i++)
	{
		cin >> num[i];
	}
	for (int i = 0;i < b; i++)
	{
		for (int j = 0;j < a; j++)
		{
			count++;
			cout << num[j * b + i];
			if (count % a != 0)
			cout << " ";
		}
		cout << endl;
	}
	delete []num;
	return 0;
}

//基礎12
#include <iostream>
using namespace std;

double f(int n)
{
	if (n == 0 || n == 1)
	return n + 1;
	else if (n > 1)
	return f(n - 1) + f(n / 2);
}

int main()
{
	int i;
	cin >> i;
	
	cout << f(i) << endl;
	return 0;
}

//基礎13
#include <iostream>
using namespace std;

double f(int n)
{
	if (n == 0 || n == 1)
	return n + 1;
	else if (n > 1)
	return f(n - 1) + f(n / 2);
}

int main()
{
	int i;
	cin >> i;
	
	cout << f(i) << endl;
	return 0;
}

//基礎19
#include <iostream>
using namespace std;

int main()
{
	int n,s,d,max;
	int time[25] = {0};
	cin >> n;
	max = 0;
	for (int i = 0;i < n; i++)
	{
		cin >> s >> d;
		for (int j = s;j < d; j++)
		{
			time[j]++;
		}
		for (int k = 0;k < 25; k++)
		{
			if (time[k] > max)
			max = time[k];
		}
	}
	cout << max << endl;
	return 0;
}


//基礎21
#include <iostream>
#include <iomanip>
using namespace std;

int main()
{
	float tmp,a,b;
	cin >> tmp;
	a = tmp;
	b = tmp;
	for (int i = 0;i < 9; i++)
	{
		cin >> tmp;
		if (tmp > a)
		{
			a = tmp;
		}
		else if (tmp < b)
		{
			b = tmp;
		}
	}
	cout << "maximum:" << fixed << setprecision(2) << a << endl;
	cout << "minimum:" << fixed << setprecision(2) << b << endl;
	return 0;
}

//基礎23
#include <iostream>
#include<string>
#include<sstream>
using namespace std;

void replacedot(string &str)
{
	int i = 0;
	while (i < str.length())
	{
		if (str[i] == ',')
		str[i] = ' ';
		i++;
	}
}

int main()
{
	string str;
	int N,a1,a2,a3,cost,x,y,z;
	N = a1 = a2 = a3 = cost = 0;
	getline(cin,str);
	replacedot(str);
	stringstream ss(str);
	ss >> N >> a1 >> a2 >> a3;
	cost = a1 * 15 + a2 * 20 + a3 * 30;
	z = (N - cost) / 50;
	y = ((N - cost) % 50) / 5;
	x = ((N - cost) % 50) % 5;
	if (cost > N)
	{
		cout << "0" << endl;
	}
	else
	{
		cout << x << "," << y << "," << z << endl;
	}
	return 0;
}


//基礎27
#include <iostream>
using namespace std;

int main()
{
	int i,a,a1,a2,a3,a4,A,B;
	cin >> a;
	i = 1;
	a4 = a % 10;
	a3 = (a / 10) % 10;
	a2 = ((a / 10) / 10) % 10;
	a1 = ((a / 10) / 10) / 10;
	bool isCorrect = false;
	while (!isCorrect)
	{
		A = 0;
		B = 0;
		cin >> i;
		if (i == 0)
		{
			isCorrect = true;
		}
		if (i != 0)
		{
			for (int j = 0;j < 4; j++)
		    {
			    if (i % 10 == a1)
			    {
				    if (j == 3)
				    {
					    A++;
				    }
				    else
				    {
					    B++;
				    }
			    }
			    else if (i % 10 == a2)
			    {
				    if (j == 2)
				    {
					    A++;
				    }
				    else
				    {
					    B++;
				    }
			    }
			    else if (i % 10 == a3)
			    {
				    if (j == 1)
				    {
					    A++;
				    }
				    else
				    {
					    B++;
				    }
			    }
			    else if (i % 10 == a4)
			    {
				    if (j == 0)
				    {
					    A++;
				    }
				    else
				    {
					    B++;
				    }
			    }
			    i /= 10;
			    if (j == 3)
		        {
			        cout << A << "A" << B << "B" << endl;
		        }
		    }
		}
	}
	return 0;
}

//基礎29
#include <iostream>
#include<string>
using namespace std;

int main()
{
	string str;
	int first,sum;
	int num[] = {10,11,12,13,14,15,16,17,34,18,19,20,21,22,35,23,24,25,26,27,28,29,32,30,31,33};
	while (getline(cin,str))
	{
		sum = 0;
		first = num[str[0] - 'A'];
		sum = (first % 10) * 9 + first / 10;//formula
		for(int i = 1;i < 9; i++)
		{
    		sum = sum + (str.at(i) - '0') * (9 - i);
    	}
    	sum = sum + (str.at(9) - '0');
    	if (sum % 10 == 0)
		{
    		cout << "CORRECT!!!" <<endl;         
		}
		else
		{
    		cout << "WRONG!!!" <<endl; 
		}
	}
	return 0;
}


//基礎30
#include<iostream>
using namespace std;

int main()
{
	int m,d;//MONTH、DAY
	cin >> m >> d;
	
	switch (m)
	{
		case 1:
			if (d >= 1 && d <= 20)
				cout << "Capricorn" << endl;
			else if (d >= 21 && d <= 31)
				cout << "Aquarius" << endl;
			break;
		case 2:
			if (d >= 1 && d <= 18)
				cout << "Aquarius" << endl;
			else if (d >= 19 && d <= 28)
				cout << "Pisces" << endl;
			break;
		case 3:
			if (d >= 1 && d <= 20)
				cout << "Pisces" << endl;
			else if (d >= 21 && d <= 31)
				cout << "Aries" << endl;
			break;
		case 4:
			if (d >= 1 && d <= 20)
				cout << "Aries" << endl;
			else if (d >= 21 && d <= 31)
				cout << "Taurus" << endl;
			break;
		case 5:
			if (d >= 1 && d <= 21)
				cout << "Taurus" << endl;
			else if (d >= 22 && d <= 31)
				cout << "Gemini" << endl;
			break;
		case 6:
			if (d >= 1 && d <= 21)
				cout << "Gemini" << endl;
			else if (d >= 22 && d <= 31)
				cout << "Cancer" << endl;
			break;
		case 7:
			if (d >= 1 && d <= 22)
				cout << "Cancer" << endl;
			else if (d >= 23 && d <= 31)
				cout << "Leo" << endl;
			break;
		case 8:
			if (d >= 1 && d <= 23)
				cout << "Leo" << endl;
			else if (d >= 24 && d <= 31)
				cout << "Virgo" << endl;
			break;
		case 9:
			if (d >= 1 && d <= 23)
				cout << "Virgo" << endl;
			else if (d >= 24 && d <= 31)
				cout << "Libra" << endl;
			break;
		case 10:
			if (d >= 1 && d <= 23)
				cout << "Libra" << endl;
			else if (d >= 24 && d <= 31)
				cout << "Scorpio" << endl;
			break;
		case 11:
			if (d >= 1 && d <= 22)
				cout << "Scorpio" << endl;
			else if (d >= 23 && d <= 31)
				cout << "Sagittarius" << endl;
			break;
		case 12:
			if (d >= 1 && d <= 21)
				cout << "Sagittarius" << endl;
			else if (d >= 22 && d <= 31)
				cout << "Capricorn" << endl;
			break;
	}
	return 0;
}

//基礎32
#include<iostream>
#include<string>
using namespace std;

int main()
{
	int n;
	string str;
	getline(cin,str);
	cin >> n;
	for (int i = 0;i < str.length(); i++)
	{
		if (str[i] >= 'A' && str[i] <= 'Z')
		str[i] = (str[i] - 'A' + n) % 26 + 'A';
		if (str[i] >= 'a' && str[i] <= 'z')
		str[i] = (str[i] - 'a' + n) % 26 + 'a';
		if (str[i] >= '0' && str[i] <= '9')
		str[i] = (str[i] - '0' + n) % 10 + '0';
	}
	cout << str << endl;
	return 0;
}

//基礎33
#include<iostream>
#include<iomanip>
#include<string>
#include<sstream>
#include<cstdlib>
using namespace std;

int main()
{
	string num[10000];
	double anum[10000];
	int size;
	double sum,avg;
	size = 0;
	sum = 0;
	avg = 0;
	string str;
	while (getline(cin,str))
	{
		stringstream ss(str);
		while (ss >> num[size])
		{
			anum[size] = atof(num[size].c_str());
			size++;
		}
		for (int i = 0;i < size; i++)
		{
			sum += anum[i];
		}
		avg = sum / size;
		cout << "Size: " << size << endl;
		cout << "Average: " << fixed << setprecision(3) << avg << endl;
		size = 0;
		sum = 0;
	}
	return 0;
}

//基礎34
#include<iostream>
#include<iomanip>
using namespace std;

int main()
{
	int height,sex;
	double weight;
	while (cin >> height >> sex)
	{
		switch (sex)
	    {
			case 1:
				weight = (height - 80) * 0.7;
				cout << fixed << setprecision(1) << weight << endl;
				break;
			case 2:
				weight = (height - 70) * 0.6;
				cout << fixed << setprecision(1) << weight << endl;
				break;
		}
	}
	return 0;
}

//基礎35
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int n, T, m, k,sum;
	int a[100];
	cin >> n;   
	for (int i = 0; i < n; i++)
	{
		cin >> T >> m >> k;
		sum = 0;
		for (int j = 0; j < k; j++)
		{
			cin >> a[j];
		}
		sort(a,a + k);
		for (int j = 0; j < m; j++)
		{
			sum += a[j];
			if (sum > T)
			break;
		}
		if (sum > T)
		{
			cout << "Impossible" << endl;
		}
		else
		{
			cout << sum << endl;
		}
	}
	return 0;
}

//36
#include<iostream>
using namespace std;

int main()
{
	int year;
	cin >> year;
	
	if (year % 400 == 0)
	{
		cout << "Bissextile Year" << endl;
	}
	else if (year % 4 == 0 && year % 100 != 0)
	{
		cout << "Bissextile Year" << endl;
	}
	else
	{
		cout << "Common Year" << endl;
	}
	return 0;
}


//37
#include<iostream>
#include<algorithm>
using namespace std;

int main()
{
	int a,b,c;
	int num[4];
	int ans[4] = {1};
	a = 0;
	b = 0;
	c = 1;
	for (int i = 0;i < 4; i++)
	cin >> num[i];
	
	sort(num, num + 4);
	for (int j = 1;j < 4; j++)
	{
		if (num[j] == num[j - 1])
		c++;
		else
		c = 1;
		ans[j] = c;
		if (a < ans[j])
		a = ans[j];
	}
	if (a == 4)
	cout << "WIN" << endl;
	else if (a == 1 || a == 3)
	cout << "R" << endl;
	else if (a == 2)
	{
		if (num[0] == num[1] && num[2] == num[3])
		{
			b = num[2] * 2;
		}
		else
		{
			for (int i = 0; i < 4; i++)
				b += num[i];
			for (int i = 0; i < 4; i++)
			if (ans[i] == a)
				b -= num[i] * 2;
		}
		cout << b << endl;
	}
	return 0;
}

//38
#include<iostream>
#include<iomanip>
using namespace std;

int main()
{
	int a;
	double x,y;
	cin >> a;
	if (a > 0)
	{
		if (a <= 120)
		{
			x = a * 2.1;
			y = a * 2.1;
		}
		else if (a > 120 && a <= 330)
	    {
	        x = 120 * 2.1 + (a - 120) * 3.02;
	        y = 120 * 2.1 + (a - 120) * 2.68;
	    }
	    else if (a > 330 && a <= 500)
	    {
		    x = 120 * 2.1 + 210 * 3.02+ (a - 330) * 4.39;
		    y = 120 * 2.1 + 210 * 2.68+ (a - 330) * 3.61;
	    }
	    else if (a > 500 && a <= 700)
	    {
		    x = 120 * 2.1 + 210 * 3.02+ 170 * 4.39+ (a - 500) * 4.97;
		    y = 120 * 2.1 + 210 * 2.68+ 170 * 3.61+ (a - 500) * 4.01;
	    }
	    else if (a > 700)
	    {
		    x = 120 * 2.1 + 210 * 3.02+ 170 * 4.39+ 200 * 4.97+ (a - 700) * 5.63;
		    y = 120 * 2.1 + 210 * 2.68+ 170 * 3.61+ 200 * 4.01+ (a - 700) * 4.50;
	    }
	    cout << "Summer months:" << fixed << setprecision(2) << x << endl;
	    cout << "Non-Summer months:" << fixed << setprecision(2) << y << endl;
	}
	return 0;
}


//39
#include <iostream>
using namespace std;

int main ()
{
	int N,sum;
	int a,b,c;
	cin >> N;

	for (int i = 0; i < N; i ++)
	{
		cin >> a >> b >> c;
		sum = a + b + c;
		if (a >= 60 && b >= 60 && c >= 60)
		{
			cout << "P" << endl;
		}
		else if (((a < 60 && b >= 60 && c >= 60) || (b < 60 && c >= 60 && a >= 60) || (c < 60 && a >= 60 && b >= 60)) && sum >= 220)
		{
			cout << "P" << endl;
		}
		else if (((a < 60 && b >= 60 && c >= 60) || (b < 60 && c >= 60 && a >= 60) || (c < 60 && a >= 60 && b >= 60)) && sum < 220)
		{
			cout << "M" << endl;
		}
		else if (((a < 60 && b < 60 && c >= 80) || (b < 60 && c < 60 && a >= 80) || (c < 60 && a < 60 && b >= 80)))
		{
			cout << "M" << endl;
		}
		else
		{
			cout << "F" << endl;
		}
	}
	return 0;
}

//40
#include<iostream>
using namespace std;

int main()
{
	int arr[10];
	char input;
	for(int j = 0;j < 10; j++) 
    { 
        cin >> input; 
        if(input != 'X') 
            arr[j] = input- '0'; 
        else 
            arr[j] = input- 78; 
    } 
    for(int k = 0;k < 2; k++) 
    { 
        for(int j = 1;j < 10; j++) 
        { 
            arr[j] = arr[j - 1] + arr[j]; 
        } 
    } 
    if(arr[9] % 11 == 0) 
        cout<< "YES" << endl; 
    else 
        cout<< "NO" << endl;
	return 0;
}

//C_ARRAY13
#include<iostream>
#include<string>
using namespace std;

int main()
{
 int M, n, num, a, b;
 int arr[10][10], ans[10][10];
 string s;
 cin >> M;
 for (int i = 0; i < M; i++)
 {
  num = 1;
  cin >> n;
  for (int x = 0; x < n; x++)
  {
   for (int y = 0; y < n; y++)
   {
    arr[x][y] = num;
    num++;
   }
  }
  getline(cin, s);
  getline(cin, s);
  for (int j = 0; j < s.length(); j++)
  {
   if (s[j] == 'R')
   {
    a = 0;
    for (int y = n - 1; y >= 0; y--)
    {
     b = 0;
     for (int x = 0; x < n; x++)
     {
      ans[x][y] = arr[a][b];
      b++;
     }
     a++;
    }
   }
   else if (s[j] == 'L')
   {
    b = n - 1;
    for (int x = 0; x < n; x++)
    {
     a = 0;
     for (int y = 0; y < n; y++)
     {
      ans[x][y] = arr[a][b];
      a++;
     }
     b--;
    }
   }
   else
   {
    a = 0;
    for (int x = n - 1; x >= 0; x--)
    {
     b = 0;
     for (int y = 0; y < n; y++)
     {
      ans[x][y] = arr[a][b];
      b++;
     }
     a++;
    }
   }
   for (int x = 0; x < n; x++)
    for (int y = 0; y < n; y++)
     arr[x][y] = ans[x][y];
  }
  for (int x = 0; x < n; x++)
  {
   for (int y = 0; y < n; y++)
   {
    if (arr[x][y] < 10)
     cout << "    " << ans[x][y];
    else if (arr[x][y] < 100)
     cout << "   " << ans[x][y];
    else
     cout << "  " << ans[x][y];
   }
   cout << endl;
  }
  if (i < M - 1)
   cout << endl;
 }
 return 0;
}


//ITSA_60第一題
#include<iostream>
using namespace std;

int main()
{
 int N,year;
 cin >> N;
 
 for (int i = 0;i < N; i++)
 {
  cin >> year;
  if (year % 400 == 0)
  {
   cout << "Bissextile Year" << endl;
  }
  else if (year % 4 == 0 && year % 100 != 0)
  {
   cout << "Bissextile Year" << endl;
  }
  else
  {
   cout << "Common Year" << endl;
  }
 }
 return 0;
}

//ITSA 60第四題
#include<iostream>
#include<string>
#include<sstream>
#include<cmath>
using namespace std;
void replacedot(string &str)
{
 int i = 0;
 while(i < str.length())
 {
  if (str[i] == '/' || str[i] == ',')
   str[i] = ' ';
  i++;
 }
}
int gcd(int a1, int a2)//球最大公因數
{
 while (a1 != a2)
 {
  if (a1 > a2)
   a1 = a1 - a2;
  else
   a2 = a2 - a1;
 }
 return a1;
}

int main()
{
 int S;
 int a1, a2, b1, b2, s1, s2;
 string str;
 cin >> S;
 getline(cin, str);
 for (int i = 0; i < S; i++)
 {
  getline(cin, str);
  replacedot(str);
  stringstream ss(str);
  ss >> a1 >> a2 >> b1 >> b2;
  s2 = a2 * b2;
  s1 = a1 * b2 + a2 * b1;
  cout << s1 / gcd(s1, s2) << "/" << s2 / gcd(s1, s2) << endl;
 }
 return 0;
}
