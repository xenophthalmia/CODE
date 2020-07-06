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

